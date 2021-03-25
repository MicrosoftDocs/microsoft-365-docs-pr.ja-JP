---
title: Jamf Pro で Microsoft Defender ATP for macOS ポリシーをセットアップする
description: Jamf Pro で Microsoft Defender ATP for macOS ポリシーをセットアップする方法について説明します。
keywords: ポリシー, microsoft, defender, atp, mac, installation, deploy, uninstallation, intune, jamfpro, macos, catalina, mojave, high sierra
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 1559d8dca6b6909f22473c5a8f4d25d4bac501d1
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51062252"
---
# <a name="set-up-the-microsoft-defender-for-endpoint-for-macos-policies-in-jamf-pro"></a>Jamf Pro で macOS 用 Microsoft Defender for Endpoint ポリシーをセットアップする

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**

- [Defender for Endpoint for Mac](microsoft-defender-endpoint-mac.md)

このページでは、Jamf Pro で macOS ポリシーを設定するために必要な手順について説明します。

次の手順を実行する必要があります。

1. [Microsoft Defender for Endpoint オンボーディング パッケージの取得](#step-1-get-the-microsoft-defender-for-endpoint-onboarding-package)

2. [オンボーディング パッケージを使用して Jamf Pro で構成プロファイルを作成する](#step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package)

3. [エンドポイントの Microsoft Defender の設定を構成する](#step-3-configure-microsoft-defender-for-endpoint-settings)

4. [Microsoft Defender for Endpoint 通知の設定を構成する](#step-4-configure-notifications-settings)

5. [Microsoft AutoUpdate (MAU) の構成](#step-5-configure-microsoft-autoupdate-mau)

6. [Microsoft Defender for Endpoint へのフル ディスク アクセスを許可する](#step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint)

7. [Microsoft Defender for Endpoint のカーネル拡張機能を承認する](#step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint)

8. [エンドポイント用 Microsoft Defender のシステム拡張機能を承認する](#step-8-approve-system-extensions-for-microsoft-defender-for-endpoint)

9. [ネットワーク拡張機能の構成](#step-9-configure-network-extension)

10. [Microsoft Defender for Endpoint for Mac でのスキャンのスケジュール設定](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp)

11. [Microsoft Defender for Endpoint for macOS の展開](#step-11-deploy-microsoft-defender-for-endpoint-for-macos)


## <a name="step-1-get-the-microsoft-defender-for-endpoint-onboarding-package"></a>手順 1: Microsoft Defender for Endpoint オンボーディング パッケージを取得する

1. [Microsoft Defender セキュリティ センターで、[](https://securitycenter.microsoft.com )オンボーディングの **設定] >移動します**。 

2. 展開方法として、オペレーティング システムとして macOS、モバイル デバイス管理 / Microsoft Intune を選択します。

    ![Microsoft Defender セキュリティ センターのイメージ](images/onboarding-macos.png)

3. [ **オンボード パッケージのダウンロード] (WindowsDefenderATPOnboardingPackage.zip)** を選択します。

4. 抽出 `WindowsDefenderATPOnboardingPackage.zip` .

5. ファイルを好みの場所にコピーします。 例: `C:\Users\JaneDoe_or_JohnDoe.contoso\Downloads\WindowsDefenderATPOnboardingPackage_macOS_MDM_contoso\jamf\WindowsDefenderATPOnboarding.plist`。


## <a name="step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package"></a>手順 2: オンボード パッケージを使用して Jamf Pro で構成プロファイルを作成する

1. 前のセクション `WindowsDefenderATPOnboarding.plist` からファイルを探します。

   ![WindowsDefenderATPOnboarding ファイルのイメージ](images/plist-onboarding-file.png)

 
2. Jamf Pro ダッシュボードで、[新規] を **選択します**。

    ![新しい Jamf Pro ダッシュボードの作成イメージ](images/jamf-pro-configure-profile.png)

3. 次の詳細を入力します。

   **全般**
   - 名前: macOS の MDATP オンボーディング
   - 説明: mDATP EDR オンボーディング for macOS
   - カテゴリ: なし
   - 配布方法: 自動的にインストールする
   - レベル: コンピューター レベル

4. [**アプリケーションの設定] &[構成] を****選択します**。

    ![アプリの構成とカスタム設定のイメージ](images/jamfpro-mac-profile.png)

5. [ファイル **のアップロード (PLIST ファイル) を選択し、[基本設定ドメイン]** **に次を** 入力します `com.microsoft.wdav.atp` 。 

    ![jamfpro plist アップロード ファイルのイメージ](images/jamfpro-plist-upload.png)

    ![アップロード ファイル プロパティリスト ファイルのイメージ](images/jamfpro-plist-file.png)

7. [開 **く] を** 選択し、オンボーディング ファイルを選択します。

    ![オンボード ファイルのイメージ](images/jamfpro-plist-file-onboard.png)

8. [アップロード **] を選択します**。 

    ![plist ファイルのアップロードのイメージ](images/jamfpro-upload-plist.png)


9. [スコープ] **タブを選択** します。

    ![[スコープのイメージ] タブ](images/jamfpro-scope-tab.png)

10. ターゲット コンピューターを選択します。

    ![ターゲット コンピューターのイメージ](images/jamfpro-target-computer.png)

    ![ターゲットのイメージ](images/jamfpro-targets.png) 

11. **[保存]** を選択します。

    ![展開ターゲット コンピューターのイメージ](images/jamfpro-deployment-target.png)

    ![選択したターゲット コンピューターのイメージ](images/jamfpro-target-selected.png)

12. [**完了**] を選択します。

    ![ターゲット グループ コンピューターのイメージ](images/jamfpro-target-group.png)

    ![構成プロファイルの一覧](images/jamfpro-configuration-policies.png)

## <a name="step-3-configure-microsoft-defender-for-endpoint-settings"></a>手順 3: エンドポイントの Microsoft Defender の設定を構成する

1.  次の Microsoft Defender for Endpoint 構成設定を使用します。

    - enableRealTimeProtection
    - passiveMode
    
    >[!NOTE]
    >既定ではオンにされません。macOS 用にサードパーティの AV を実行する予定の場合は、 に設定します `true` 。

    - 除外
    - excludedPath
    - excludedFileExtension
    - excludedFileName
    - exclusionsMergePolicy
    - allowedThreats
    
    >[!NOTE]
    >EICAR はサンプルに含め、概念実証を行う場合は、EICAR をテストする場合は特に削除してください。
        
    - disallowedThreatActions
    - potentially_unwanted_application
    - archive_bomb
    - cloudService
    - automaticSampleSubmission
    - tags
    - hideStatusMenuIcon
    
     詳細については [、「Jamf 構成プロファイルのプロパティ 一覧」を参照してください](mac-preferences.md#property-list-for-jamf-configuration-profile)。

     ```XML
     <?xml version="1.0" encoding="UTF-8"?>
     <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
     <plist version="1.0">
     <dict>
         <key>antivirusEngine</key>
         <dict>
             <key>enableRealTimeProtection</key>
             <true/>
             <key>passiveMode</key>
             <false/>
             <key>exclusions</key>
             <array>
                 <dict>
                     <key>$type</key>
                     <string>excludedPath</string>
                     <key>isDirectory</key>
                     <false/>
                     <key>path</key>
                     <string>/var/log/system.log</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedPath</string>
                     <key>isDirectory</key>
                     <true/>
                     <key>path</key>
                     <string>/home</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedFileExtension</string>
                     <key>extension</key>
                     <string>pdf</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedFileName</string>
                     <key>name</key>
                     <string>cat</string>
                 </dict>
             </array>
             <key>exclusionsMergePolicy</key>
             <string>merge</string>
             <key>allowedThreats</key>
             <array>
                 <string>EICAR-Test-File (not a virus)</string>
             </array>
             <key>disallowedThreatActions</key>
             <array>
                 <string>allow</string>
                 <string>restore</string>
             </array>
             <key>threatTypeSettings</key>
             <array>
                 <dict>
                     <key>key</key>
                     <string>potentially_unwanted_application</string>
                     <key>value</key>
                     <string>block</string>
                 </dict>
                 <dict>
                     <key>key</key>
                     <string>archive_bomb</string>
                     <key>value</key>
                     <string>audit</string>
                 </dict>
             </array>
             <key>threatTypeSettingsMergePolicy</key>
             <string>merge</string>
         </dict>
         <key>cloudService</key>
         <dict>
             <key>enabled</key>
             <true/>
             <key>diagnosticLevel</key>
             <string>optional</string>
             <key>automaticSampleSubmission</key>
             <true/>
         </dict>
         <key>edr</key>
         <dict>
             <key>tags</key>
             <array>
                 <dict>
                     <key>key</key>
                     <string>GROUP</string>
                     <key>value</key>
                     <string>ExampleTag</string>
                 </dict>
             </array>
         </dict>
         <key>userInterface</key>
         <dict>
             <key>hideStatusMenuIcon</key>
             <false/>
         </dict>
     </dict>
     </plist>
     ```

2. ファイルをとして保存します `MDATP_MDAV_configuration_settings.plist` 。


3.  Jamf Pro ダッシュボードで、[全般] を **選択します**。

    ![新しい Jamf Pro ダッシュボードのイメージ](images/644e0f3af40c29e80ca1443535b2fe32.png)

4. 次の詳細を入力します。

    **全般**
    
    - 名前: MDATP MDAV 構成設定
    - 説明:\<blank\>
    - カテゴリ: なし (既定)
    - 配布方法: 自動インストール(既定)
    - Level: Computer Level(default)

    ![MDATP MDAV 構成設定のイメージ](images/3160906404bc5a2edf84d1d015894e3b.png)

5. [**アプリケーションの設定] &[構成] を****選択します**。

    ![アプリとカスタム設定のイメージ](images/e1cc1e48ec9d5d688087b4d771e668d2.png)

6. [ファイル **のアップロード] (PLIST ファイル) を選択します**。

    ![構成設定 plist ファイルのイメージ](images/6f85269276b2278eca4bce84f935f87b.png)

7. [ **基本設定ドメイン] で、「PLIST** `com.microsoft.wdav` ファイルのアップロード  **」と入力し、[アップロード] を選択します**。

    ![構成設定の基本設定ドメインのイメージ](images/db15f147dd959e872a044184711d7d46.png)

8. [ファイル **の選択] を選択します**。

    ![構成設定のイメージファイルを選択する](images/526e978761fc571cca06907da7b01fd6.png)

9. **[MDATP_MDAV_configuration_settings.plist] を選択し、[** 開く] を **選択します**。

    ![mdatpmdav 構成設定のイメージ](images/98acea3750113b8dbab334296e833003.png)

10. [アップロード **] を選択します**。

    ![構成設定のアップロードのイメージ](images/0adb21c13206861ba9b30a879ade93d3.png)

    ![構成設定のアップロード イメージのイメージ](images/f624de59b3cc86e3e2d32ae5de093e02.png)

    >[!NOTE]
    >Intune ファイルをアップロードすると、次のようなエラー メッセージが表示されます。<br>
    >![構成設定 intune ファイルのアップロードのイメージ](images/8e69f867664668796a3b2904896f0436.png)


11. **[保存]** を選択します。 

    ![構成設定のイメージ 画像を保存する](images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png)

12. ファイルがアップロードされます。

    ![構成設定ファイルアップロード画像の画像](images/33e2b2a1611fdddf6b5b79e54496e3bb.png)

    ![アップロードされた構成設定ファイルのイメージ](images/a422e57fe8d45689227e784443e51bd1.png)

13. [スコープ] **タブを選択** します。

    ![構成設定スコープのイメージ](images/9fc17529e5577eefd773c658ec576a7d.png)

14. **[Contoso's Machine Group] を選択します**。 

15. [追加 **] を** 選択し、[保存] **を選択します**。

    ![構成設定のイメージを追加する](images/cf30438b5512ac89af1d11cbf35219a6.png)

    ![構成設定の保存のイメージの追加](images/6f093e42856753a3955cab7ee14f12d9.png)

16. [**完了**] を選択します。 新しい構成プロファイルが **表示されます**。

    ![構成設定の構成プロファイル イメージのイメージ](images/dd55405106da0dfc2f50f8d4525b01c8.png)


## <a name="step-4-configure-notifications-settings"></a>手順 4: 通知の設定を構成する

これらの手順は、macOS 10.15 (Catalina) 以降に適用できます。

1. `notif.mobileconfig` [GitHub リポジトリからダウンロードする](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/notif.mobileconfig)

2. として保存します `MDATP_MDAV_notification_settings.plist` 。

3. Jamf Pro ダッシュボードで、[全般] を **選択します**。 
       
4. 次の詳細を入力します。

    **全般** 
    
    - 名前: MDATP MDAV 通知の設定
    - 説明: macOS 10.15 (Catalina) 以降
    - カテゴリ: なし (既定)
    - 配布方法: 自動インストール(既定)
    - Level: Computer Level(default)

    ![構成設定 mdatpmdav のイメージ](images/c9820a5ff84aaf21635c04a23a97ca93.png)


5. [ファイル **のアップロード] (PLIST ファイル) を選択します**。

    ![構成設定アップロード plistfile のイメージ](images/7f9138053dbcbf928e5182ee7b295ebe.png)
 

6. [**ファイルの選択]**  >  **MDATP_MDAV_Notification_Settings.plist を選択します**。


    ![構成設定 mdatpmdav notsettings のイメージ](images/4bac6ce277aedfb4a674f2d9fcb2599a.png)


    ![構成設定 mdatpmdav notifsettings のイメージ](images/20e33b98eb54447881dc6c89e58b890f.png)

7. [アップロード **を開く]**  >  **を選択します**。

    ![構成設定 upl img のイメージ](images/7697c33b9fd376ae5a8023d01f9d3857.png)


    ![構成設定 upl イメージのイメージ](images/2bda9244ec25d1526811da4ea91b1c86.png)

8. [スコープ] **タブを選択** し、[追加] を **選択します**。

    ![構成設定スコープの追加のイメージ](images/441aa2ecd36abadcdd8aed03556080b5.png)


9. **[Contoso's Machine Group] を選択します**。 

10. [追加 **] を** 選択し、[保存] **を選択します**。
    
    ![構成設定 contoso machine grp save のイメージ](images/09a275e321268e5e3ac0c0865d3e2db5.png)

    
    ![構成設定のイメージの保存の追加](images/4d2d1d4ee13d3f840f425924c3df0d51.png)

11. [**完了**] を選択します。 新しい構成プロファイルが **表示されます**。
    ![構成設定完了 img のイメージ](images/633ad26b8bf24ec683c98b2feb884bdf.png)

## <a name="step-5-configure-microsoft-autoupdate-mau"></a>手順 5: Microsoft AutoUpdate (MAU) を構成する

1. 次の Microsoft Defender for Endpoint 構成設定を使用します。

      ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
   <plist version="1.0">
   <dict>
    <key>ChannelName</key>
    <string>Current</string>
    <key>HowToCheck</key>
    <string>AutomaticDownload</string>
    <key>EnableCheckForUpdatesButton</key>
    <true/>
    <key>DisableInsiderCheckbox</key>
    <false/>
    <key>SendAllTelemetryEnabled</key>
    <true/>
   </dict>
   </plist>
   ```

2. として保存します `MDATP_MDAV_MAU_settings.plist` 。

3. Jamf Pro ダッシュボードで、[全般] を **選択します**。 

    ![構成設定の一般的なイメージのイメージ](images/eaba2a23dd34f73bf59e826217ba6f15.png)

4. 次の詳細を入力します。

    **全般** 
    
    - 名前: MDATP MDAV MAU の設定
    - 説明: MacOS 用 MDATP の Microsoft AutoUpdate 設定
    - カテゴリ: なし (既定)
    - 配布方法: 自動インストール(既定)
    - Level: Computer Level(default)

5. [**アプリケーションの設定] &[構成] を****選択します**。

    ![構成設定アプリとカスタム設定のイメージ](images/1f72e9c15eaafcabf1504397e99be311.png)

6. [ファイル **のアップロード] (PLIST ファイル) を選択します**。

    ![構成設定 plist のイメージ](images/1213872db5833aa8be535da57653219f.png)  

7. [基本 **設定ドメイン]** に「:」 `com.microsoft.autoupdate2` と入力し **、[PLIST ファイルのアップロード] を選択します**。

    ![構成設定のプリフェッチ ドメインのイメージ](images/1213872db5833aa8be535da57653219f.png)

8. [ファイル **の選択] を選択します**。

    ![構成設定の選択ファイルのイメージ](images/335aff58950ce62d1dabc289ecdce9ed.png)

9. **[MDATP_MDAV_MAU_settings.plist] を選択します**。

    ![構成設定 mdatpmdavmau 設定のイメージ](images/a26bd4967cd54bb113a2c8d32894c3de.png)

10. [アップロード **] を選択します**。
    ![構成設定 uplimage のイメージ](images/4239ca0528efb0734e4ca0b490bfb22d.png)

    ![構成設定 uplimg のイメージ](images/4ec20e72c8aed9a4c16912e01692436a.png)

11. **[保存]** を選択します。

    ![構成設定 saveimg のイメージ](images/253274b33e74f3f5b8d475cf8692ce4e.png)

12. [スコープ] **タブを選択** します。
   
     ![構成設定 scopetab のイメージ](images/10ab98358b2d602f3f67618735fa82fb.png)

13. **[追加]** を選択します。
    
    ![構成設定 addimg1 のイメージ](images/56e6f6259b9ce3c1706ed8d666ae4947.png)

    ![構成設定 addimg2 のイメージ](images/38c67ee1905c4747c3b26c8eba57726b.png)

    ![構成設定 addimg3 のイメージ](images/321ba245f14743c1d5d51c15e99deecc.png)

14. [**完了**] を選択します。
    
    ![構成設定 doneimage のイメージ](images/ba44cdb77e4781aa8b940fb83e3c21f7.png)

## <a name="step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint"></a>手順 6: エンドポイント用 Microsoft Defender へのフル ディスク アクセスを許可する

1. Jamf Pro ダッシュボードで、[構成プロファイル **] を選択します**。

    ![構成設定構成プロファイルのイメージ](images/264493cd01e62c7085659d6fdc26dc91.png)

2. [+ **新規] を選択します**。 

3. 次の詳細を入力します。

    **全般** 
    - 名前: MDATP MDAV - EDR および AV へのフル ディスク アクセスを許可する
    - 説明: macOS Catalina 以降では、新しいプライバシー設定ポリシーコントロール
    - カテゴリ: なし
    - 配布方法: 自動的にインストールする
    - レベル: コンピューター レベル


    ![構成設定全般のイメージ](images/ba3d40399e1a6d09214ecbb2b341923f.png)

4. [ **プライバシー設定の構成] ポリシーコントロールで、[構成** ] を **選択します**。

    ![構成のプライバシー ポリシー制御のイメージ](images/715ae7ec8d6a262c489f94d14e1e51bb.png)

5. [ **プライバシー設定ポリシー制御] で、** 次の詳細を入力します。

    - 識別子: `com.microsoft.wdav`
    - 識別子の種類: バンドル ID
    - コード要件: `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`


    ![構成設定のプライバシー設定ポリシー制御の詳細のイメージ](images/22cb439de958101c0a12f3038f905b27.png)

6. **[+ 追加]** を選択します。

    ![構成設定のイメージ システム ポリシーのすべてのファイルを追加する](images/bd93e78b74c2660a0541af4690dd9485.png)

    - [アプリまたはサービス] で **、SystemPolicyAllFiles に設定する**

    - [アクセス] の下: [許可] に **設定します。**

7. [ **保存]** を選択します (右下の保存は選択しない)。

    ![構成設定の保存イメージのイメージ](images/6de50b4a897408ddc6ded56a09c09fe2.png)

8. [アプリ アクセス `+` ] の横にある **記号をクリックして** 、新しいエントリを追加します。

    ![構成設定アプリアクセスのイメージ](images/tcc-add-entry.png)

9. 次の詳細を入力します。

    - 識別子: `com.microsoft.wdav.epsext`
    - 識別子の種類: バンドル ID
    - コード要件: `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

10. **[+ 追加]** を選択します。

    ![構成設定 tcc epsext エントリのイメージ](images/tcc-epsext-entry.png)

    - [アプリまたはサービス] で **、SystemPolicyAllFiles に設定する**

    - [アクセス] の下: [許可] に **設定します。**

11. [ **保存]** を選択します (右下の保存は選択しない)。

    ![構成設定 tcc epsext image2 のイメージ](images/tcc-epsext-entry2.png)

12. [スコープ] **タブを選択** します。

    ![構成設定スコープのイメージ](images/2c49b16cd112729b3719724f581e6882.png)

13. **[+ 追加]** を選択します。

    ![構成設定のイメージ addimage](images/57cef926d1b9260fb74a5f460cee887a.png)

14. [ **グループ名]** > [コンピューター グループ] **を** 選択> **Contoso の MachineGroup を選択します**。 

    ![構成設定 contoso machinegrp のイメージ](images/368d35b3d6179af92ffdbfd93b226b69.png)

15. **[追加]** を選択します。 

16. **[保存]** を選択します。 
    
17. [**完了**] を選択します。
    
    ![構成設定 donimg のイメージ](images/809cef630281b64b8f07f20913b0039b.png)
    
    ![構成設定 donimg2 のイメージ](images/6c8b406ee224335a8c65d06953dc756e.png)


## <a name="step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint"></a>手順 7: Microsoft Defender for Endpoint のカーネル拡張機能を承認する

1. [構成プロファイル **] で、[+** 新規 **] を選択します**。

    ![自動的に生成されたソーシャル メディア投稿の説明のスクリーンショット](images/6c8b406ee224335a8c65d06953dc756e.png)

2. 次の詳細を入力します。

    **全般** 
    
    - 名前: MDATP MDAV カーネル拡張機能
    - 説明: MDATP カーネル拡張機能 (kext)
    - カテゴリ: なし
    - 配布方法: 自動的にインストールする
    - レベル: コンピューター レベル

    ![構成設定 mdatpmdav カーネルのイメージ](images/24e290f5fc309932cf41f3a280d22c14.png)

3. [承認済 **みカーネル拡張機能の構成] で、[構成** ] を **選択します**。

    ![構成設定承認済みカーネル ext のイメージ](images/30be88b63abc5e8dde11b73f1b1ade6a.png)

   
4. [ **承認済みカーネル拡張機能]** で、次の詳細を入力します。

    - 表示名: Microsoft Corp.
    - チーム ID: UBF8T346G9

    ![構成設定 appr カーネル拡張機能のイメージ](images/39cf120d3ac3652292d8d1b6d057bd60.png)

5. [スコープ] **タブを選択** します。

    ![構成設定スコープ タブ img のイメージ](images/0df36fc308ba569db204ee32db3fb40a.png)

6. **[+ 追加]** を選択します。

7. [ **グループ名]** > [コンピューター グループ] **を>** Contoso の [コンピューター グループ] **を選択します**。

8. **[+ 追加]** を選択します。

    ![構成設定のイメージにイメージを追加する](images/0dde8a4c41110dbc398c485433a81359.png)

9. **[保存]** を選択します。

    ![構成設定の saveimag のイメージ](images/0add8019b85a453b47fa5c402c72761b.png)

10. [**完了**] を選択します。

    ![doneimag の構成設定のイメージ](images/1c9bd3f68db20b80193dac18f33c22d0.png)


## <a name="step-8-approve-system-extensions-for-microsoft-defender-for-endpoint"></a>手順 8: エンドポイント用 Microsoft Defender のシステム拡張機能を承認する

1. [構成プロファイル **] で、[+** 新規 **] を選択します**。

    ![自動的に生成されたソーシャル メディア投稿の説明のスクリーンショット](images/6c8b406ee224335a8c65d06953dc756e.png)

2. 次の詳細を入力します。

    **全般**
    
    - 名前: MDATP MDAV システム拡張機能
    - 説明: MDATP システム拡張機能
    - カテゴリ: なし
    - 配布方法: 自動的にインストールする
    - レベル: コンピューター レベル

    ![構成設定 sysext new prof のイメージ](images/sysext-new-profile.png)

3. [ **システム拡張機能] で、[構成** ] を **選択します**。

   ![構成設定 sysext config のイメージ](images/sysext-configure.png)

4. [System **Extensions] に次** の詳細を入力します。

   - 表示名: Microsoft Corp. System Extensions
   - システム拡張の種類: 許可されているシステム拡張機能
   - チーム識別子: UBF8T346G9
   - 許可されるシステム拡張機能:
     - **com.microsoft.wdav.epsext**
     - **com.microsoft.wdav.netext**

    ![構成設定 sysextconfig2 のイメージ](images/sysext-configure2.png)

5. [スコープ] **タブを選択** します。

    ![構成設定 scopeimage のイメージ](images/0df36fc308ba569db204ee32db3fb40a.png)

6. **[+ 追加]** を選択します。

7. [ **グループ名]** > [コンピューター グループ] **を>** Contoso の [コンピューター グループ] **を選択します**。

8. **[+ 追加]** を選択します。

   ![構成設定 addima のイメージ](images/0dde8a4c41110dbc398c485433a81359.png)

9. **[保存]** を選択します。

   ![構成設定 sysext スコープのイメージ](images/sysext-scope.png)

10. [**完了**] を選択します。

    ![構成設定 sysext-final のイメージ](images/sysext-final.png)

## <a name="step-9-configure-network-extension"></a>手順 9: ネットワーク拡張機能を構成する

エンドポイント検出と応答機能の一環として、Microsoft Defender for Endpoint for Mac はソケット トラフィックを検査し、この情報を Microsoft Defender セキュリティ センター ポータルに報告します。 次のポリシーでは、ネットワーク拡張機能でこの機能を実行できます。

>[!NOTE]
>JAMF にはコンテンツ フィルター ポリシーの組み込みのサポートが用意されていません。これは、Microsoft Defender for Endpoint for Mac がデバイスにインストールするネットワーク拡張機能を有効にするための前提条件です。 さらに、JAMF は展開するポリシーの内容を変更する場合があります。
>そのため、次の手順では、構成プロファイルに署名する回避策を提供します。

1. `netfilter.mobileconfig` [GitHub リポジトリからデバイスにダウンロード](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/netfilter.mobileconfig)し、次のように保存します。`com.microsoft.network-extension.mobileconfig`

2. JAMF の組 [み込](https://www.jamf.com/jamf-nation/articles/649/creating-a-signing-certificate-using-jamf-pro-s-built-in-certificate-authority) みの証明機関を使用して署名証明書を作成するには、このページの指示に従います。

3. 証明書を作成してデバイスにインストールしたら、macOS デバイスからターミナルから次のコマンドを実行します。

   ```bash
   $ security cms -S -N "<certificate name>" -i com.microsoft.network-extension.mobileconfig -o com.microsoft.network-extension.signed.mobileconfig
   ```

   ![署名済み構成を作成するコマンドを含むターミナル ウィンドウ](images/netext-create-profile.png)

4. JAMF ポータルから [構成プロファイル] に移動 **し、[** アップロード] ボタン **をクリック** します。 

   ![アップロード ウィンドウのイメージ](images/netext-upload-file.png)

5. [ファイル **の選択] を選択** し、 を選択します `microsoft.network-extension.signed.mobileconfig` 。

   ![アップロード ウィンドウのイメージ netext choose file](images/netext-choose-file.png)

6. [アップロード **] を選択します**。

   ![アップロード ウィンドウ netext アップロード ファイル 2 の画像](images/netext-upload-file2.png)

7. ファイルをアップロードすると、新しいページにリダイレクトされ、このプロファイルの作成が完了します。

   ![新しい構成プロファイル netext プロファイル ページのイメージ](images/netext-profile-page.png)

8. [スコープ] **タブを選択** します。

   ![[構成設定] [sco] タブのイメージ](images/0df36fc308ba569db204ee32db3fb40a.png)

9. **[+ 追加]** を選択します。

10. [ **グループ名]** > [コンピューター グループ] **を>** Contoso の [コンピューター グループ] **を選択します**。

11. **[+ 追加]** を選択します。

    ![構成設定 adim のイメージ](images/0dde8a4c41110dbc398c485433a81359.png)

12. **[保存]** を選択します。

    ![構成設定のイメージ savimg netextscop](images/netext-scope.png)

13. [**完了**] を選択します。

    ![構成設定 netextfinal のイメージ](images/netext-final.png)

## <a name="step-10-schedule-scans-with-microsoft-defender-for-endpoint-for-mac"></a>手順 10: Microsoft Defender for Endpoint for Mac でスキャンをスケジュールする
「Microsoft Defender [for Endpoint for Mac でスキャンをスケジュールする」の手順に従います](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp)。

## <a name="step-11-deploy-microsoft-defender-for-endpoint-for-macos"></a>手順 11: Microsoft Defender for Endpoint for macOS を展開する

1. 保存した場所に移動します `wdav.pkg` 。

    ![エクスプローラー wdav pkg のイメージ](images/8dde76b5463047423f8637c86b05c29d.png)

2. に名前を変更します `wdav_MDM_Contoso_200329.pkg` 。

    ![エクスプローラー 1 wdavmdmpkg のイメージ](images/fb2220fed3a530f4b3ef36f600da0c27.png)

3. Jamf Pro ダッシュボードを開きます。

    ![構成設定 jamfpro のイメージ](images/990742cd9a15ca9fdd37c9f695d1b9f4.png)

4. コンピューターを選択し、上部の歯車アイコンをクリックし、[コンピューターの管理] **を選択します**。

    ![構成設定 compmgmt のイメージ](images/b6d671b2f18b89d96c1c8e2ea1991242.png)

5. [パッケージ **] で**、[+ **新規] を選択します**。 
    ![Bird Description が自動的に生成されたパッケージ new を含む図](images/57aa4d21e2ccc65466bf284701d4e961.png)

6. [ **新しいパッケージ]** で、次の詳細を入力します。

    **[全般] タブ**
    - 表示名: 空白のままにしておきます。 pkg を選択するとリセットされます。
    - カテゴリ: なし (既定)
    - ファイル名: [ファイル] を選択します。

    ![[構成設定のイメージ] [全般] タブ](images/21de3658bf58b1b767a17358a3f06341.png)

    ファイルを開き、またはをポイント `wdav.pkg` します `wdav_MDM_Contoso_200329.pkg` 。
    
    ![コンピューター画面のスクリーンショット 説明が自動的に生成される](images/1aa5aaa0a387f4e16ce55b66facc77d1.png)

7. [**開く**]を選択します。 [表示名 **] を** **[Microsoft Defender Advanced Threat Protection] および [Microsoft Defender ウイルス対策] に設定します**。

    **マニフェスト ファイル** は必須ではありません。 Microsoft Defender Advanced Threat Protection はマニフェスト ファイルなしで動作します。
    
    **オプション タブ**<br> 既定値を保持します。

    **[制限] タブ**<br> 既定値を保持します。
    
     ![[構成設定の制限] タブのイメージ](images/56dac54634d13b2d3948ab50e8d3ef21.png)
   
8. **[保存]** を選択します。 パッケージは Jamf Pro にアップロードされます。 

   ![構成設定パック upl jamf pro のイメージ](images/33f1ecdc7d4872555418bbc3efe4b7a3.png)

   パッケージを展開に使用するには数分かかる場合があります。
   
   ![構成設定パック upl のイメージ](images/1626d138e6309c6e87bfaab64f5ccf7b.png)

9. [ポリシー] **ページに移動** します。

    ![構成設定のポロのイメージ](images/f878f8efa5ebc92d069f4b8f79f62c7f.png)

10. [+ **新規] を** 選択して新しいポリシーを作成します。

    ![構成設定の新しいポリシーのイメージ](images/847b70e54ed04787e415f5180414b310.png)


11. [ **全般]** 次の詳細を入力します。

    - 表示名: MDATP Onboarding Contoso 200329 v100.86.92 以降

    ![構成設定のイメージmdatponboard ](images/625ba6d19e8597f05e4907298a454d28.png)

12. [ **定期的なチェックイン] を選択します**。 
    
    ![構成設定の再チェック インのイメージ](images/68bdbc5754dfc80aa1a024dde0fce7b0.png)

  
13. **[保存]** を選択します。 
 
14. [パッケージ **] を選択>構成します**。
 
    ![構成設定パック構成のイメージ](images/8fb4cc03721e1efb4a15867d5241ebfb.png)

15. [Microsoft **Defender Advanced Threat** Protection] と [Microsoft Defender ウイルス対策] の横にある **[追加] ボタンを選択します**。

    ![構成設定 MDATP と MDA の追加のイメージ](images/526b83fbdbb31265b3d0c1e5fbbdc33a.png)

16. **[保存]** を選択します。

    ![構成設定のイメージsavimg](images/9d6e5386e652e00715ff348af72671c6.png)

17. [スコープ] **タブを選択** します。  

    ![構成設定 scptab のイメージ](images/8d80fe378a31143db9be0bacf7ddc5a3.png)

18. ターゲット コンピューターを選択します。

    ![構成設定 tgtcomp のイメージ](images/6eda18a64a660fa149575454e54e7156.png)

    **Scope**
    
    **[追加]** を選択します。
    
    ![構成設定 ad1img のイメージ](images/1c08d097829863778d562c10c5f92b67.png)

    ![構成設定 ad2img のイメージ](images/216253cbfb6ae738b9f13496b9c799fd.png)

    **セルフサービス**
    
    ![構成設定セルフサービスのイメージ](images/c9f85bba3e96d627fe00fc5a8363b83a.png)

19. [**完了**] を選択します。 

    ![構成設定 do1img のイメージ](images/99679a7835b0d27d0a222bc3fdaf7f3b.png)

    ![構成設定 do2img のイメージ](images/632aaab79ae18d0d2b8e0c16b6ba39e2.png)



