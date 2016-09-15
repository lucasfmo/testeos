<properties
	pageTitle="Azure Mobile Engagement iOS SDK 整合"
	description="Azure Mobile Engagement iOS SDK 的最新更新與程序"
	services="mobile-engagement"
	documentationCenter="mobile"
	authors="MehrdadMzfr"
	manager="dwrede"
	editor="" />

<tags
	ms.service="mobile-engagement"
	ms.workload="mobile"
	ms.tgt_pltfrm="mobile-ios"
	ms.devlang="objective-c"
	ms.topic="article"
	ms.date="08/19/2016"
	ms.author="MehrdadMzfr" />

#如何在 iOS 上整合 Engagement

> [AZURE.SELECTOR]
- [Windows Universal](mobile-engagement-windows-store-integrate-engagement.md)
- [Windows Phone Silverlight](mobile-engagement-windows-phone-integrate-engagement.md)
- [iOS](mobile-engagement-ios-integrate-engagement.md)
- [Android](mobile-engagement-android-integrate-engagement.md)

此程序描述在您的 iOS 應用程式中，啟動 Engagement 的分析和監視功能時，最簡單的方法。

> [AZURE.IMPORTANT] Engagement SDK 需要 iOS6 以上：應用程式的部署目標必須至少為 iOS 6。

下列步驟便足以啟用計算使用者、工作階段、活動、當機和技術相關的所有統計資料需要的記錄檔之報告。用來計算事件、錯誤及工作等其他統計資料所需的記錄檔報告必須使用 Engagement API 手動完成 (請參閱[如何在 iOS 應用程式中使用進階的 Mobile Engagement 標記 API](mobile-engagement-ios-use-engagement-api.md))，因為這些是與應用程式相依的統計資料。

##將 Engagement SDK 嵌入您的 iOS 專案

從[這裡](http://aka.ms/qk2rnj)下載 iOS SDK。
將 Engagement SDK 加入您的 iOS 專案：在 Xcode 中，以滑鼠右鍵按一下專案，然後選取 [**新增檔案至**]，再選擇 `EngagementSDK` 資料夾。

Engagement 需要額外的架構才能運作：在專案總管中，開啟專案窗格並選取正確的目標。然後，開啟 [建置階段] 索引標籤，在 [連結二進位檔與程式庫] 功能表中加入下列架構：

> -   `AdSupport.framework`：將連結設為`Optional`
> -   `SystemConfiguration.framework`
> -   `CoreTelephony.framework`
> -   `CFNetwork.framework`
> -   `CoreLocation.framework`
> -   `libxml2.dylib`

> [AZURE.NOTE] AdSupport 架構可以移除。Engagement 需要此架構來收集 IDFA。但您可以停用 IDFA 集合 \<ios-sdk-engagement-idfa\>，以符合關於此識別碼的新 Apple 原則。

##初始化 Engagement SDK

您需要修改應用程式委派：

-   在實作檔案頂端匯入 Engagement 代理程式：

		[...]
		#import "EngagementAgent.h"

-   在 '**applicationDidFinishLaunching:**' 或 '**application:didFinishLaunchingWithOptions:**' 方法內初始化 Engagement：

		- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
		{
		  [...]
		  [EngagementAgent init:@"Endpoint={YOUR_APP_COLLECTION.DOMAIN};SdkKey={YOUR_SDK_KEY};AppId={YOUR_APPID}"];
		  [...]
		}

##基本報告

### 建議使用的方法：多載您的 `UIViewController` 類別

若要啟動 Engagement 需要的所有記錄檔報告，來計算使用者、工作階段、活動、當機和技術統計資料，您只需要讓所有 `UIViewController` 子類別繼承自 `EngagementViewController` 類別 (`UITableViewController` -> `EngagementTableViewController` 也是相同的規則)。

**沒有 Engagement：**

	#import <UIKit/UIKit.h>

	@interface Tab1ViewController : UIViewController<UITextFieldDelegate> {
	  UITextField* myTextField1;
	  UITextField* myTextField2;
	}

	@property (nonatomic, retain) IBOutlet UITextField* myTextField1;
	@property (nonatomic, retain) IBOutlet UITextField* myTextField2;

**有 Engagement：**
