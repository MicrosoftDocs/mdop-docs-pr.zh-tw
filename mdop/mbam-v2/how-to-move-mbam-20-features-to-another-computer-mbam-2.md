---
title: 如何將 MBAM 2.0 功能移到其他電腦
description: 如何將 MBAM 2.0 功能移到其他電腦
author: dansimp
ms.assetid: 49bc0792-60a4-473f-89cc-ada30191e04a
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, security
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 340d87e26d87f124a9ab64c63d33e89c293d8a86
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "10810940"
---
# 如何將 MBAM 2.0 功能移到其他電腦


本主題說明將一或多個 Microsoft BitLocker 管理和監控（MBAM）功能移至不同電腦時應採取的步驟。 在移動一個以上的 Microsoft BitLocker 管理和監視功能時，您應該依下列順序移動它們：

1.  復原資料庫

2.  合規性和審核資料庫

3.  合規性與審計報告

4.  管理和監控

## 移動恢復資料庫


若要將復原資料庫從一部電腦移到另一台電腦（例如，從伺服器 A 移至伺服器 B），請使用下列程式。

1.  停止管理和監控網站的所有實例。

2.  在伺服器 B 上執行 MBAM 安裝程式。

3.  在伺服器 A 上備份 MBAM 修復資料庫。

4.  將 MBAM 復原資料庫從伺服器 A 移至 B。

5.  在伺服器 B 上還原 MBAM 修復資料庫。

6.  在伺服器 B 上設定對 MBAM 復原資料庫的存取權。

7.  更新 MBAM 管理和監視伺服器上的資料庫連線資料。

8.  繼續 MBAM 管理和監視網站的所有實例。

**停止 MBAM 管理和監視網站的所有實例**

1.  在執行 MBAM 管理和監視功能的每個伺服器上，使用 Internet Information Services （IIS）管理員主控台來停止名為**Microsoft BitLocker 管理和監視**的 MBAM 網站。

2.  若要自動化此程式，您可以使用 Windows PowerShell 來輸入類似以下的命令列：

    `PS C:\> Stop-Website “Microsoft BitLocker Administration and Monitoring”`

    **注意**  
    若要執行此 PowerShell 命令列，必須將 PowerShell 的 IIS 模組新增到目前的 PowerShell 實例。 此外，您必須更新 PowerShell 執行原則，以啟用腳本執行。



**在伺服器 B 上執行 MBAM 設定**

1.  在伺服器 B 上執行 MBAM 安裝程式，然後只選取要安裝的復原**資料庫**。

2.  若要自動化此程式，您可以使用 Windows PowerShell 來輸入類似以下的命令列：

    `PS C:\> MbamSetup.exe /qn I_ACCEPT_ENDUSER_LICENSE_AGREEMENT=1 AddLocal=KeyDatabase ADMINANDMON_MACHINENAMES=$DOMAIN$\$SERVERNAME$$ RECOVERYANDHWDB_SQLINSTANCE=$SERVERNAME$\$SQLINSTANCENAME$ TOPOLOGY=$X$`

    **注意**  
    在上述範例中，將下列值取代為符合您環境的專案：

    -   $SERVERNAME $ \ \ $SQLINSTANCENAME $-輸入要將恢復資料庫移動到其中的伺服器和實例名稱。

    -   $DOMAIN $ \ \ $SERVERNAME $-輸入將會與恢復資料庫聯絡的每個 MBAM 管理和監視伺服器的網域和伺服器名稱。 使用分號來分隔清單中的每個網域和伺服器配對（例如，$DOMAIN \\SERVERNAME $; $DOMAIN \\ $SERVERNAME $ $）。 每個伺服器名稱後面必須加一個 "$" 符號，如下例所示（MyDomain\\MyServerName1 $;MyDomain\\MyServerName2 $）。

    -   如果您要安裝 MBAM 獨立拓朴，請 $X $-輸入**0** ; 如果您要安裝 MBAM Configuration Manager 拓撲，則為**1** 。



**在伺服器 A 上備份恢復資料庫**

1.  若要在伺服器 A 上備份復原資料庫，請使用 SQL Server Management Studio 及名為 Back 的工作。 根據預設，資料庫名稱是 MBAM 的 [**恢復資料庫**]。

2.  若要自動化此程式，請建立包含下列 SQL 腳本的 SQL 檔案（.sql）：

    修改 MBAM 復原資料庫，以使用完整的復原模式。

    ```sql
    USE master;

    GO

    ALTER DATABASE "MBAM Recovery and Hardware"

       SET RECOVERY FULL;

    GO

    -- Create MBAM Recovery Database Data and MBAM Recovery logical backup devices.

    USE master

    GO

    EXEC sp_addumpdevice 'disk', 'MBAM Recovery and Hardware Database Data Device',

    'Z:\MBAM Recovery Database Data.bak';

    GO

    -- Back up the full MBAM Recovery Database.

    BACKUP DATABASE [MBAM Recovery and Hardware] TO [MBAM Recovery and Hardware Database Data Device];

    GO

    BACKUP CERTIFICATE [MBAM Recovery Encryption Certificate]

    TO FILE = 'Z:\SQLServerInstanceCertificateFile'

    WITH PRIVATE KEY

    (

        FILE = ' Z:\SQLServerInstanceCertificateFilePrivateKey',

        ENCRYPTION BY PASSWORD = '$PASSWORD$'

    );

    GO
    ```

    **注意**  
    在上述範例中，將下列值取代為符合您環境的專案：

    -   $PASSWORD $-輸入將用來加密私密金鑰檔案的密碼。



3.  使用 SQL Server PowerShell 和類似下列的命令列來執行 SQL 檔案：

    `PS C:\> Invoke-Sqlcmd -InputFile 'Z:\BackupMBAMRecoveryandHardwarDatabaseScript.sql' -ServerInstance $SERVERNAME$\$SQLINSTANCENAME$`

    **注意**  
    在上述範例中，將下列值取代為符合您環境的專案：

    -   $SERVERNAME $ \ \ $SQLINSTANCENAME $-輸入將備份恢復資料庫的伺服器和實例名稱。



**從伺服器 A 將復原資料庫和憑證移至伺服器 B**

1.  使用 Windows 資源管理器，將下列檔案從伺服器 A 移至伺服器 B。

    -   MBAM 恢復資料庫資料 .bak

2.  若要移動加密資料庫的憑證，請使用下列自動化步驟。 若要自動化此程式，您可以使用 Windows PowerShell 輸入類似以下的命令列：

    `PS C:\> Copy-Item “Z:\MBAM Recovery Database Data.bak” \\$SERVERNAME$\$DESTINATIONSHARE$`

    `PS C:\> Copy-Item “Z:\SQLServerInstanceCertificateFile” \\$SERVERNAME$\$DESTINATIONSHARE$`

    `PS C:\> Copy-Item “Z:\SQLServerInstanceCertificateFilePrivateKey” \\$SERVERNAME$\$DESTINATIONSHARE$`

    **注意**  
    在上述範例中，將下列值取代為符合您環境的專案：

    -   $SERVERNAME $-輸入要將檔案複製到其中的伺服器名稱。

    -   $DESTINATIONSHARE $-輸入要將檔案複製到其中的共用名稱稱和路徑。



**在伺服器 B 上還原恢復資料庫**

1.  在伺服器 B 上使用 SQL Server Management Studio 及名為 [**還原資料庫**] 的工作來還原恢復資料庫。

2.  完成工作後，請選取 [**發件**人] 選項，然後使用 [Add] （**新增**）命令選取 MBAM 復原資料庫**資料 .bak**盤案，以選取資料庫備份檔案。

3.  選取 **[確定]** 以完成還原程式。

4.  若要自動化此程式，請建立包含下列 SQL 腳本的 SQL 檔案（.sql）：

    ```sql
    -- Restore MBAM Recovery Database. 

    USE master

    GO

    -- Drop certificate created by MBAM Setup.

    DROP CERTIFICATE [MBAM Recovery Encryption Certificate]

    GO

    --Add certificate

    CREATE CERTIFICATE [MBAM Recovery Encryption Certificate]

    FROM FILE = 'Z: \SQLServerInstanceCertificateFile'

    WITH PRIVATE KEY

    (

        FILE = ' Z:\SQLServerInstanceCertificateFilePrivateKey',

        DECRYPTION BY PASSWORD = '$PASSWORD$'

    );

    GO

    -- Restore the MBAM Recovery Database data and log files.

    RESTORE DATABASE [MBAM Recovery and Hardware]

       FROM DISK = 'Z:\MBAM Recovery Database Data.bak'

       WITH REPLACE
    ```

    **注意**  
    在上述範例中，將下列值取代為符合您環境的專案：

    -   $PASSWORD $-輸入您用來加密私人金鑰檔案的密碼。



5.  您可以使用 Windows PowerShell 來輸入類似以下的命令列：

    `PS C:\> Invoke-Sqlcmd -InputFile 'Z:\RestoreMBAMRecoveryandHardwarDatabaseScript.sql' -ServerInstance $SERVERNAME$\$SQLINSTANCENAME$`

    **注意**  
    在上述範例中，將下列值取代為符合您環境的專案：

    -   $SERVERNAME $ \ \ $SQLINSTANCENAME $-輸入將還原恢復資料庫的伺服器和實例名稱。



**在伺服器 B 上設定存取恢復資料庫**

1.  在伺服器 B 上，使用 [伺服器管理員] 中的 [本機使用者和群組] 管理單元，將執行 MBAM 管理和監控功能的每個伺服器上的電腦帳戶新增到名為**MBAM 復原及硬體資料庫存取權**的本機群組。

2.  確認已還原的資料庫上的 SQL 登入**MBAM 復原及硬體 Db 存取**已對應至 [登入名稱] **$MachineName $ \\MBAM 復原與硬體資料庫存取**。 如果未如所述對應，請使用類似的群組成員資格建立另一個登入，然後將它對應至登入名稱 **$MachineName $ \\MBAM 復原與硬體資料庫存取**。

3.  若要自動化此程式，您可以在伺服器 B 上使用 Windows PowerShell，輸入類似以下的命令列：

    `PS C:\> net localgroup "MBAM Recovery and Hardware DB Access" $DOMAIN$\$SERVERNAME$$  /add`

    **注意**  
    請以適用于您環境的值取代上述範例中的下列值：

    -   $DOMAIN $ \ \ $SERVERNAME $ $-輸入 MBAM 管理和監視伺服器的網域和電腦名稱稱。 伺服器名稱必須後接 $，如範例中所示（例如，MyDomain\\MyServerName1 $）。



~~~
This command line must be run for each Administration and Monitoring Server that will be accessing the database in your environment.
~~~

**更新 MBAM 管理和監視伺服器上的復原資料庫連線資料**

1. 在執行 MBAM 管理和監視功能的每個伺服器上，使用 Internet Information Services （IIS）管理員主控台來更新下列應用程式的連線字串資訊，這些應用程式是託管于 [管理] 和 [監視] 網站：

   -   MBAMAdministrationService

   -   MBAMRecoveryAndHardwareService

2. 選取每個應用程式，並使用 [設定**編輯器**] 功能（位於**功能視圖**的 [**管理**] 區段底下）。

3. 從**區段清單**控制項選取 [ **configurationStrings** ] 選項。

4. 選取名為 **（集合）** 的列，然後選取列右側的按鈕來開啟**集合編輯器**。

5. 在**集合編輯器**中，更新 MBAMAdministrationService 應用程式的設定或名為 Mbam 的列時，請選取名為**KeyRecoveryConnectionString**的列 <strong> 。 </strong>更新 MBAMRecoveryAndHardwareService 的設定時的 ConnectionString。

6. 更新**configurationStrings**屬性的**資料來源 =** 值，以列出伺服器名稱和實例（例如，$SERVERNAME $ \ \ $SQLINSTANCENAME $），並將恢復資料庫移至該伺服器。

7. 若要自動化此程式，您可以在每個管理和監視伺服器上使用 Windows 輸入命令列，這與下列類似：

   `PS C:\> Set-WebConfigurationProperty '/connectionStrings/add[@name="KeyRecoveryConnectionString"]' -PSPath "IIS:\sites\Microsoft Bitlocker Administration and Monitoring\MBAMAdministrationService" -Name "connectionString" -Value “Data Source=$SERVERNAME$\$SQLINSTANCENAME$;Initial Catalog=MBAM Recovery and Hardware;Integrated Security=SSPI;”`

   `PS C:\> Set-WebConfigurationProperty '/connectionStrings/add[@name="Microsoft.Mbam.RecoveryAndHardwareDataStore.ConnectionString"]' -PSPath "IIS:\sites\Microsoft Bitlocker Administration and Monitoring\MBAMRecoveryAndHardwareService" -Name "connectionString" -Value "Data Source=$SERVERNAME$\$SQLINSTANCENAME$;Initial Catalog=MBAM Recovery and Hardware;Integrated Security=SSPI;"`

   **注意**  
   在上述範例中，將下列值取代為符合您環境的專案：

   -   $SERVERNAME $ \ \ $SQLINSTANCENAME $-輸入恢復資料庫的伺服器名稱和實例。



**繼續 MBAM 管理和監視網站的所有實例**

1.  在執行 MBAM 管理和監視功能的每個伺服器上，使用 Internet Information Services （IIS）管理員主控台來啟動名為**Microsoft BitLocker 管理和監視**的 MBAM 網站。

2.  若要自動化此程式，您可以使用 Windows PowerShell 輸入類似以下的命令列：

    `PS C:\> Start-Website “Microsoft BitLocker Administration and Monitoring”`

## 移動合規性與審計資料庫功能


如果您想要將 MBAM 合規性和審核資料庫從一部電腦移到另一台電腦（也就是將資料庫從伺服器 A 移至伺服器 B），請使用下列程式。 此套裝程式含下列高層次步驟：

1.  停止管理和監控網站的所有實例。

2.  在伺服器 B 上執行 MBAM 安裝程式。

3.  在伺服器 A 上備份資料庫。

4.  將資料庫從伺服器 A 移至 B。

5.  在伺服器 B 上還原資料庫。

6.  在伺服器 B 上設定對資料庫的存取權。

7.  更新 MBAM 管理和監視伺服器上的資料庫連線資料。

8.  使用合規性和審核資料庫的新位置來更新 SSRS 報表資料來源連線字串。

9.  繼續所有管理和監控網站的實例。

**停止管理和監控網站的所有實例**

1.  在執行 MBAM 管理和監視功能的每個伺服器上，使用 Internet Information Services （IIS）管理員主控台來停止名為**Microsoft BitLocker 管理及監視**的 MBAM 網站。

2.  若要自動化此程式，您可以使用 Windows PowerShell 輸入類似以下的命令列：

    `PS C:\> Stop-s “Microsoft BitLocker Administration and Monitoring”`

    **注意**  
    若要執行此命令列，您必須將 PowerShell 的 IIS 模組新增至目前的 PowerShell 實例。 此外，您必須更新 PowerShell 執行原則，才能執行腳本。



**在伺服器 B 上執行 MBAM 設定**

1.  在伺服器 B 上執行 MBAM 安裝程式，然後只選取**合規性和審核資料庫**以進行安裝。

2.  若要自動化此程式，您可以使用 Windows PowerShell 輸入類似以下的命令列：

    `PS C:\> MbamSetup.exe /qn I_ACCEPT_ENDUSER_LICENSE_AGREEMENT=1 AddLocal= ReportsDatabase ADMINANDMON_MACHINENAMES=$DOMAIN$\$SERVERNAME$ COMPLIDB_SQLINSTANCE=$SERVERNAME$\$SQLINSTANCENAME$ REPORTS_USERACCOUNT=$DOMAIN$\$USERNAME$ TOPOLOGY=$X$`

    **注意**  
    注意：請將上述範例中的下列值取代成與您的環境相符的值：

    -   $SERVERNAME $ \ \ $SQLINSTANCENAME $-輸入要將合規性和審核資料庫移至其中的伺服器名稱和實例。

    -   $DOMAIN $ \ \ $SERVERNAME $-輸入將會與合規性和審核資料庫聯繫的每個 MBAM 管理和監視伺服器的網域和伺服器名稱。 使用分號來分隔清單中的每個網域和伺服器對（例如，$DOMAIN \\SERVERNAME $; $DOMAIN \\ $SERVERNAME $ $）。 每個伺服器名稱後面必須加一個 "$" 符號，如下例所示（MyDomain\\MyServerName1 $;MyDomain\\MyServerName2 $）。

    -   $DOMAIN $ \ \ $USERNAME $-輸入將由合規性和審核報告功能用來連線至合規性和審核資料庫的網域和使用者名稱。

    -   如果您要安裝 MBAM 獨立拓朴，請 $X $-輸入**0** ; 如果您要安裝 MBAM Configuration Manager 拓撲，則為**1** 。



**在伺服器 A 上備份合規性和審核資料庫**

1.  若要在伺服器 A 上備份合規性和審核資料庫，請使用 SQL Server Management Studio 及名為**back**的工作。 根據預設，資料庫名稱是**MBAM 合規性狀態資料庫**。

2.  若要自動化此程式，請建立包含下列 SQL 腳本的 SQL 檔案（.sql）：

    ```sql
    -- Modify the MBAM Compliance Status Database to use the full recovery model.

    USE master;

    GO

    ALTER DATABASE "MBAM Compliance Status"

       SET RECOVERY FULL;

    GO

    -- Create MBAM Compliance Status Data logical backup devices.

    USE master

    GO

    EXEC sp_addumpdevice 'disk', 'MBAM Compliance Status Database Data Device',

    'Z: \MBAM Compliance Status Database Data.bak';

    GO

    -- Back up the full MBAM Recovery database.

    BACKUP DATABASE [MBAM Compliance Status] TO [MBAM Compliance Status Database Data Device];

    GO
    ```

3.  使用與下列類似的 Windows PowerShell 命令列來執行 SQL 檔案：

    `PS C:\> Invoke-Sqlcmd -InputFile "Z:\BackupMBAMComplianceStatusDatabaseScript.sql" –ServerInstance $SERVERNAME$\$SQLINSTANCENAME$`

    **注意**  
    在上述範例中，將下列值取代為符合您環境的專案：

    -   $SERVERNAME $ \ \ $SQLINSTANCENAME $-輸入要備份合規性和審核資料庫的伺服器名稱和實例。



**將合規性和審核資料庫從伺服器 A 移至 B**

1.  使用 Windows 資源管理器，將下列檔案從伺服器 A 移至伺服器 B。

    -   MBAM 合規性狀態資料庫資料 .bak

2.  若要自動化此程式，您可以使用 Windows PowerShell 輸入類似以下的命令列：

    `PS C:\> Copy-Item “Z:\MBAM Compliance Status Database Data.bak” \\$SERVERNAME$\$DESTINATIONSHARE$`

    **注意**  
    在上述範例中，將下列值取代為符合您環境的專案：

    -   $SERVERNAME $-輸入要將檔案複製到其中的伺服器名稱。

    -   $DESTINATIONSHARE $-輸入要將檔案複製到其中的共用名稱稱和路徑。



**在伺服器 B 上還原合規性和審核資料庫**

1.  在伺服器 B 上使用 SQL Server Management Studio 及名為 [**還原資料庫**] 的工作來還原合規性和審核資料庫。

2.  完成工作後，請選取 [**發件**人] 選項，然後使用 [Add] （**新增**）命令選取 MBAM 合規性狀態資料庫資料 .bak 檔案。 選取 **[確定]** 以完成還原程式。

3.  若要自動化此程式，請建立包含下列 SQL 腳本的 SQL 檔案（.sql）：

    ```sql
    -- Create MBAM Compliance Status Database Data logical backup devices. 

    Use master

    GO

    -- Restore the MBAM Compliance Status database data files.

    RESTORE DATABASE [MBAM Compliance Status]

       FROM DISK = 'C:\test\MBAM Compliance Status Database Data.bak'

       WITH REPLACE
    ```

4.  使用與下列類似的 Windows PowerShell 命令列來執行 SQL 檔案：

    `PS C:\> Invoke-Sqlcmd -InputFile "Z:\RestoreMBAMComplianceStatusDatabaseScript.sql" -ServerInstance $SERVERNAME$\$SQLINSTANCENAME$`

    **注意**  
    在上述範例中，將下列值取代為符合您環境的專案：

    -   $SERVERNAME $ \ \ $SQLINSTANCENAME $-輸入要將合規性和審核資料庫還原至其中的伺服器名稱和實例。



**在伺服器 B 上設定對合規性和審核資料庫的存取權**

1.  在伺服器 B 上，使用 [伺服器管理員] 中的 [本機使用者和群組] 管理單元，將執行 MBAM 管理和監控功能的每個伺服器上的電腦帳戶新增到名為 [ **MBAM 合規性狀態 DB 存取**] 的本機群組。

2.  確認 SQL 登入**MBAM 相容性審核資料庫存取**已還原的資料庫已對應至登入名稱 **$MACHINENAME $ \\ MBAM 合規性審核資料庫存取**。 如果未如所述對應，請使用類似的群組成員資格建立另一個登入，然後將它對應至登入名稱 **$MachineName $ \ \ MBAM 合規性審核資料庫存取**。

3.  若要自動化此程式，您可以使用 Windows PowerShell 在伺服器 B 上輸入如下所示的命令列：

    `PS C:\> net localgroup "MBAM Compliance Auditing DB Access" $DOMAIN$\$SERVERNAME$$  /add`

    `PS C:\> net localgroup "MBAM Compliance Auditing DB Access" $DOMAIN$\$REPORTSUSERNAME$  /add`

    **注意**  
    請以適用于您環境的值取代上述範例中的下列值：

    -   $DOMAIN $ \ \ $SERVERNAME $ $-輸入 MBAM 管理和監視伺服器的網域和電腦名稱稱。 伺服器名稱必須後接「$」，如範例所示。 （例如，MyDomain\\MyServerName1 $）

    -   $DOMAIN $ \ \ $REPORTSUSERNAME $-輸入用來設定合規性和審核報告之資料來源的使用者帳戶名稱。



~~~
The command line for adding the servers to the MBAM Compliance and Audit Database access local group must be run for each Administration and Monitoring Server that will be accessing the database in your environment.
~~~

**更新 MBAM 管理和監視伺服器上的資料庫連線資料**

1.  在執行 MBAM 管理和監視功能的每個伺服器上，使用 Internet Information Services （IIS）管理員主控台來更新下列應用程式的連線字串資訊，這些應用程式是託管于 [管理] 和 [監視] 網站：

    -   MBAMAdministrationService

    -   MBAMComplianceStatusService

2.  選取每個應用程式，並使用 [設定**編輯器**] 功能（位於**功能視圖**的 [**管理**] 區段底下）。

3.  從**區段清單**控制項選取 [ **configurationStrings** ] 選項。

4.  選取名為 **（集合）** 的列，然後選取列右側的按鈕來開啟**集合編輯器**。

5.  在**集合編輯器**中，更新 MBAMAdministrationService 應用程式的設定時，請選取名為**ComplianceStatusConnectionString**的列，或者在更新 MBAMComplianceStatusService 的設定時，選取名為**BitLockerManagement**的列。

6.  更新**configurationStrings**屬性的**資料來源 =** 值，以列出已將復原資料庫移動到其中的伺服器和實例名稱（例如 $SERVERNAME $ \ \ $SQLINSTANCENAME）。

7.  若要自動化此程式，您可以使用 Windows 在與下列類似的每個管理和監視伺服器上輸入命令列：

    `PS C:\> Set-WebConfigurationProperty '/connectionStrings/add[@name="ComplianceStatusConnectionString"]' -PSPath "IIS:\sites\Microsoft Bitlocker Administration and Monitoring\MBAMAdministrationService" -Name "connectionString" -Value "Data Source=$SERVERNAME$\$SQLINSTANCENAME$;Initial Catalog=MBAM Compliance Status;Integrated Security=SSPI;"`

    `PS C:\> Set-WebConfigurationProperty '/connectionStrings/add[@name="Microsoft.Windows.Mdop.BitLockerManagement.StatusReportDataStore.ConnectionString"]' -PSPath "IIS:\sites\Microsoft Bitlocker Administration and Monitoring\MBAMComplianceStatusService" -Name "connectionString" -Value "Data Source=$SERVERNAME$\$SQLINSTANCENAME;Initial Catalog=MBAM Compliance Status;Integrated Security=SSPI;"`

    **注意**  
    在上述範例中，將下列值取代為符合您環境的專案：

    -   $SERVERNAME $ \ \ $SQLINSTANCENAME $-輸入恢復資料庫所在的伺服器名稱和實例。



**繼續 MBAM 管理和監視網站的所有實例**

1.  在執行 MBAM 管理和監視功能的每個伺服器上，使用 Internet Information Services （IIS）管理員主控台來啟動名為**Microsoft BitLocker 管理和監視**的 MBAM 網站。

2.  若要自動化此程式，您可以使用 Windows PowerShell 輸入類似以下的命令列：

    `PS C:\> Start-Website “Microsoft BitLocker Administration and Monitoring”`

## 移動合規性與審計報告


如果您想要將 MBAM 合規性和審核報告從一部電腦移到另一台電腦（也就是將報表從伺服器 A 移至伺服器 B），請使用下列程式，其中包含下列高級步驟：

1.  在伺服器 B 上執行 MBAM 安裝程式。

2.  在伺服器 B 上設定對合規性和審核報告的存取權。

3.  停止 MBAM 管理和監視網站的所有實例。

4.  更新 MBAM 管理和監視伺服器上的報表連線資料。

5.  繼續 MBAM 管理和監視網站的所有實例。

**在伺服器 B 上執行 MBAM 設定**

1.  在伺服器 B 上執行 MBAM 安裝程式，然後只選取 [**合規性] 和 [審核報告**] 功能進行安裝。

2.  若要自動化此程式，您可以使用 Windows PowerShell 輸入類似以下的命令列：

    `PS C:\> MbamSetup.exe /qn I_ACCEPT_ENDUSER_LICENSE_AGREEMENT=1 AddLocal=Reports COMPLIDB_SQLINSTANCE=$SERVERNAME$\$SQLINSTANCENAME$ REPORTS_USERACCOUNTPW=$PASSWORD$ TOPOLOGY=$X$`

    **注意**  
    在上述範例中，將下列值取代為符合您環境的專案：

    -   $SERVERNAME $ \ \ $SQLINSTANCENAME $-輸入合規性和審核資料庫所在的伺服器名稱和實例。

    -   $DOMAIN $ \ \ $USERNAME $-輸入將由合規性和審核報告功能用來連線至合規性和審核資料庫的網域和使用者名稱。

    -   $PASSWORD $-輸入將用來連線至合規性和審核資料庫之使用者帳戶的密碼。

    -   如果您要安裝 MBAM 獨立拓朴，請 $X $-輸入**0** ; 如果您要安裝 MBAM Configuration Manager 拓撲，則為**1** 。



**在伺服器 B 上設定合規性和審核報告的存取權**

1.  在伺服器 B 上，使用 [伺服器管理員] 中的 [本機使用者和群組] 管理單元，新增能夠存取合規性和審核報告的使用者帳戶。 將使用者帳戶新增到名為 MBAM 報告使用者的本機群組。

2.  若要自動化此程式，您可以使用 Windows PowerShell 在伺服器 B 上輸入如下所示的命令列：

    `PS C:\> net localgroup "MBAM Report Users" $DOMAIN$\$REPORTSUSERNAME$  /add`

    **注意**  
    請以適用于您環境的值取代上述範例中的下列值：

    -   $DOMAIN $ \ \ $REPORTSUSERNAME $-輸入用來設定合規性和審核報告之資料來源的使用者帳戶名稱。



~~~
The command line for adding the users to the MBAM Report Users local group must be run for each user that will be accessing the reports in your environment.
~~~

**停止 MBAM 管理和監視網站的所有實例**

1.  在執行 MBAM 管理和監視伺服器功能的每個伺服器上，使用 Internet Information Services （IIS）管理員主控台來停止名為**Microsoft BitLocker 管理和監視**的 MBAM 網站。

2.  若要自動化此程式，您可以使用 Windows PowerShell 輸入類似以下的命令列：

    `PS C:\> Stop-Website “Microsoft BitLocker Administration and Monitoring”`

**更新 MBAM 管理和監視伺服器上的資料庫連線資料**

1. 在執行 MBAM 管理和監視伺服器功能的每個伺服器上，使用 [網際網路資訊服務（IIS）管理員] 主控台來更新合規性和審核報告 URL。

2. 選取 [ **Microsoft BitLocker 管理及監視**網站]，然後使用 [**功能] 視圖**[**管理**] 區段底下的 [設定**編輯器**] 功能。

3. 從**區段清單**控制項選取 [ **appSettings** ] 選項。

4. 選取名為 **（集合）** 的列，然後選取列右側的按鈕來開啟**集合編輯器**。

5. 在**集合編輯器**中，選取名為**Mbam**的資料列。

6. 更新**Mbam**的值，以反映伺服器 B 的伺服器名稱。如果 [規範] 和 [審核報告] 功能已安裝在命名的 SQL Reporting Services 實例上，請務必在 URL 中新增或更新實例的名稱（例如，HTTP://$SERVERNAME $/ReportServer\_ $ SQLSRSINSTANCENAME $/Pages....）

7. 若要自動化此程式，您可以使用 Windows PowerShell，在與下列類似的每個管理和監視伺服器上輸入命令列：

   `PS C:\> Set-WebConfigurationProperty '/appSettings/add[@key="Microsoft.Mbam.Reports.Url"]' -PSPath "IIS:\ \sites\Microsoft Bitlocker Administration and Monitoring\HelpDesk" -Name "Value" -Value “http://$SERVERNAME$/ReportServer_$SRSINSTANCENAME$/Pages/ReportViewer.aspx?/ Microsoft+BitLocker+Administration+and+Monitoring/”`

   **注意**  
   在上述範例中，將下列值取代為符合您環境的專案：

   -   $SERVERNAME $-輸入已安裝 [合規性] 與 [審核報告] 的伺服器名稱。

   -   $SRSINSTANCENAME $-輸入已安裝合規性和審核報告之 SQL Reporting Services 實例的名稱。



**繼續 MBAM 管理和監視網站的所有實例**

1.  在執行 MBAM 管理和監視伺服器功能的每個伺服器上，使用 Internet Information Services （IIS）管理員主控台來啟動名為**Microsoft BitLocker 管理和監視**的 MBAM 網站。

2.  若要自動化此程式，您可以使用 Windows PowerShell 輸入類似以下的命令列：

    `PS C:\> Start-Website “Microsoft BitLocker Administration and Monitoring”`

    **注意**  
    若要執行此命令列，您必須將 PowerShell 的 IIS 模組新增至目前的 PowerShell 實例。 此外，您必須更新 PowerShell 執行原則，才能執行腳本。



## 移動 [管理及監視] 功能


如果您想要將 MBAM 管理和監控報告功能從一部電腦移到另一台電腦（也就是將功能從伺服器 A 移到伺服器 B），請使用下列程式，其中包括下列高級步驟：

1.  在伺服器 B 上執行 MBAM 安裝程式。

2.  在伺服器 B 上設定對資料庫的存取權。

**在伺服器 B 上執行 MBAM 設定**

1.  在伺服器 B 上執行 MBAM 安裝程式，然後只選取 [**管理及監視伺服器**] 功能進行安裝。

2.  若要自動化此程式，您可以使用 Windows PowerShell 輸入類似以下的命令列：

    `PS C:\> MbamSetup.exe /qn I_ACCEPT_ENDUSER_LICENSE_AGREEMENT=1 AddLocal=AdministrationMonitoringServer, COMPLIDB_SQLINSTANCE=$SERVERNAME$\$SQLINSTANCENAME$ RECOVERYANDHWDB_SQLINSTANCE=$SERVERNAME$\$SQLINSTANCENAME$ SRS_REPORTSITEURL=$REPORTSSERVERURL$ TOPOLOGY=$X$`

    **注意**  
    在上述範例中，將下列值取代為符合您環境的專案：

    -   $SERVERNAME $ \ \ $SQLINSTANCENAME $-若為 COMPLIDB \ _SQLINSTANCE 參數，請輸入合規性和審核資料庫所在的伺服器名稱和實例。 針對 RECOVERYANDHWDB \ _SQLINSTANCE 參數，輸入恢復資料庫所在的伺服器名稱和實例。

    -   $DOMAIN $ \ \ $USERNAME $-輸入將由合規性和審核報告功能用來連線至合規性和審核資料庫的網域和使用者名稱。

    -   $ REPORTSSERVERURL $-輸入 SQL Reporting Services 網站之家用位置的 URL。 如果報告已安裝到預設的 SRS 實例，URL 格式將會採用「HTTP://$SERVERNAME $/ReportServer」格式。 如果報告已安裝到預設的 SRS 實例，URL 格式的格式會為「HTTP://$SERVERNAME $/ReportServer\_ $ SQLINSTANCENAME $」。

    -   如果您要安裝 MBAM 獨立拓朴，請 $X $-輸入**0** ; 如果您要安裝 MBAM Configuration Manager 拓撲，則為**1** 。



**設定資料庫的存取權**

1.  在已部署復原資料庫及合規性和審核資料庫的伺服器上，請使用 [伺服器管理員] 中的 [本機使用者和群組] 管理單元，將執行 MBAM 管理和監視伺服器功能的每個伺服器上的電腦帳戶新增到名為 MBAM 復原與**硬體資料庫存取**（復原 DB 伺服器）及**MBAM 合規性狀態 DB 存取**（合規性和審核資料庫伺服器）的

2.  若要自動化此程式，您可以使用 Windows PowerShell，在部署合規性和審核資料庫的伺服器上，輸入如下所示的命令列。

    `PS C:\> net localgroup "MBAM Compliance Auditing DB Access" $DOMAIN$\$SERVERNAME$$  /add`

3.  在部署復原資料庫的伺服器上，您可以使用 Windows PowerShell 來輸入類似以下的命令列：

    `PS C:\> net localgroup "MBAM Recovery and Hardware DB Access" $DOMAIN$\$SERVERNAME$$  /add`

    **注意**  
    將上述範例中的下列值取代為您的環境適用的值：

    -   $DOMAIN $ \ \ $SERVERNAME $ $-輸入管理和監視伺服器的網域和電腦名稱稱。 伺服器名稱必須後接 "$" 符號，如範例中所示（例如，MyDomain\\MyServerName1 $）。

    -   $DOMAIN $ \ \ $REPORTSUSERNAME $-輸入用來設定合規性和審核報告之資料來源的使用者帳戶名稱。



~~~
The command lines that are listed for adding server computer accounts to the MBAM local groups must be run for each Administration and Monitoring Server that will be accessing the databases in your environment.
~~~

## 相關主題


[維護 MBAM 2.0](maintaining-mbam-20-mbam-2.md)









