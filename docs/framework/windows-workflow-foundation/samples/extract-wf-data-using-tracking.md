---
title: 使用跟踪提取 WF 数据
ms.date: 03/30/2017
ms.assetid: e30c68f5-8c6a-495a-bd20-667a4364c68e
ms.openlocfilehash: ef8118df2c5834e32c40760ef31f75660893d89b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501578"
---
# <a name="extract-wf-data-using-tracking"></a>使用跟踪提取 WF 数据
此示例演示如何使用工作流跟踪从活动中提取工作流变量和自变量。 它还演示如何为跟踪记录添加批注以及如何从自定义跟踪记录中提取数据负载。 此示例使用 Windows 事件跟踪 (ETW) 跟踪参与者来提取工作流中的数据。  
  
## <a name="sample-details"></a>示例详细信息  
 Windows Workflow Foundation (WF) 提供了跟踪，以深入了解工作流实例的执行。 跟踪运行时在工作流执行过程中会发出工作流跟踪记录。 除工作流跟踪记录以外，还可以从工作流提取工作流实例中的数据。 下面的列表详述了可从跟踪记录中提取的数据的类型：  
  
1.  活动中的工作流变量和活动执行过程中的跟踪记录。  
  
     为了提取工作流变量，将在一个配置文件中指定要提取的变量。 只能使用 `ActivityStateQueries` 来指定要提取的变量。 下面的代码示例演示用于从活动中提取工作流变量的跟踪配置文件。  
  
    ```xml  
    <activityStateQuery activityName="StockPriceService">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <variables>  
              <variable name="symbol"/>  
         </variables>  
    </activityStateQuery>  
    ```  
  
2.  活动参数和活动状态跟踪记录。  
  
     参数可定义数据流入或流出活动的方式。 使用 <xref:System.Activities.Tracking.ActivityStateQuery> 来指定要提取的参数。下面的代码示例是一个提取 `Value` 参数的跟踪配置文件。  
  
    ```xml  
    <activityStateQuery activityName="GetStockPrice">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <arguments>  
              <argument name="Value"/>  
         </arguments>  
    </activityStateQuery>  
    ```  
  
3.  批注是可添加到发出的任何跟踪记录的键/值对。  
  
     批注用作跟踪记录的标记机制。 通过跟踪配置文件将批注添加到跟踪记录中。 可将批注添加到任何类型的工作流跟踪查询中。 下面的代码示例是一个跟踪配置文件，它演示如何将批注添加到跟踪记录中。  
  
    ```xml  
    <workflowInstanceQuery>  
         <states>  
              <state name="Started"/>  
         </states>  
         <annotations>  
              <annotation name="StockPriceWorkflow" value="Begin"/>  
         </annotations>  
    </workflowInstanceQuery>  
    ```  
  
4.  从用户定义的活动发出自定义跟踪记录。  
  
     自定义跟踪记录可包含此活动中定义的负载数据。 通过订阅跟踪配置文件中的自定义跟踪记录，可从跟踪记录中提取负载。 可使用自定义 <xref:System.Activities.Tracking.TrackingQuery> 来提取自定义跟踪记录。 下面的代码示例是一个跟踪配置文件，它将提取自定义跟踪记录及其负载。  
  
    ```xml  
    <customTrackingQuery name="QuoteLookupEvent" activityName="GetStockPrice"/>  
    ```  
  
 此示例演示如何使用 Web.config 中指定的配置文件来提取变量、参数和自定义记录，以及添加批注。通过添加 `<etwTracking>` 行为元素对示例工作流服务启用跟踪。 下面的代码示例为 `ExtractWorkflowVariables` 跟踪配置文件启用了跟踪。  
  
```xml  
<serviceBehaviors>  
     <behavior>  
               <etwTracking profileName="ExtractWorkflowVariables"/>  
     </behavior>  
</serviceBehaviors>  
```  
  
#### <a name="to-use-this-sample"></a>使用此示例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 打开 WFStockPriceApplication.sln 解决方案文件。  
  
2.  要生成解决方案，按 Ctrl+Shift+B。  
  
3.  若要运行解决方案，请按 F5。  
  
     浏览器窗口打开和显示侦听应用程序的目录。  
  
4.  在浏览器中，单击 StockPriceService.xamlx。  
  
5.  浏览器显示 StockPriceService 页，其中包含本地服务 WSDL 地址。 复制此地址。  
  
     下面的示例演示本地服务 WSDL 地址。 `http://localhost:53797/StockPriceService.xamlx?wsdl`  
  
6.  在调用服务之前，请启动事件查看器并确保事件日志正在侦听从工作流服务发出的跟踪事件。  
  
7.  从**启动**菜单中，选择**管理工具**，然后**事件查看器**。  
  
8.  在事件查看器中树视图中，导航到**事件查看器**，**应用程序和服务日志**，并**Microsoft**。 右键单击**Microsoft** ，然后选择**视图**，然后**显示分析和调试日志**。  
  
     絋粄**显示分析和调试日志**选项处于选中状态。  
  
9. 在事件查看器中树视图中，导航到**事件查看器**，**应用程序和服务日志**， **Microsoft**， **Windows**， **应用程序服务器-应用程序**。 右键单击**Analytic** ，然后选择**启用日志**。  
  
10. 使用 [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]，打开 WCF 测试客户端。  
  
     WCF 测试客户端 (WcfTestClient.exe) 位于\<[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]安装文件夹 > \Common7\IDE\ 文件夹。  
  
     默认的 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 安装文件夹为 C:\Program Files\Microsoft Visual Studio 10.0。  
  
11. 在 WCF 测试客户端，选择**添加的服务**从**文件**菜单。  
  
     在输入框中添加您先前复制的本地服务 WSDL 地址。  
  
12. 在 WCF 测试客户端中，双击 `GetStockPrice`。  
  
     这会打开 `GetStockPrice` 方法。 此请求会接受一个参数。 使用值**Contoso**。  
  
13. 单击**调用**。  
  
14. 切换回事件查看器并导航到**事件查看器**，**应用程序和服务日志**， **Microsoft**， **Windows**， **应用程序服务器-应用程序**。 右键单击**Analytic** ，然后选择**刷新**。 工作流事件的事件 ID 位于 100-199 范围内。  
  
     事件包含批注、变量、参数和自定义跟踪记录，可在事件查看器中查看这些内容。  
  
## <a name="cleaning-up-in-the-event-viewer"></a>清除事件查看器中的内容  
 通过执行以下操作，可在事件查看器中清除事件日志中的分析通道。  
  
#### <a name="to-clean-up-optional"></a>清理（可选）  
  
1.  打开事件查看器。  
  
2.  导航到**事件查看器**，**应用程序和服务日志**， **Microsoft**， **Windows**，**应用程序服务器应用程序**。 右键单击**Analytic** ，然后选择**禁用日志**。  
  
3.  导航到**事件查看器**，**应用程序和服务日志**， **Microsoft**， **Windows**，**应用程序服务器应用程序**。 右键单击**Analytic** ，然后选择**清除日志**。  
  
     选择**清除**选项可清除这些事件。  
  
## <a name="known-issue"></a>已知问题  
  
> [!NOTE]
>  事件查看器中存在一个已知问题，即可能无法解码 ETW 事件。 您可能会看到与下面类似的错误消息。  
>   
>  `The description for Event ID <id> from source Microsoft-Windows-Application Server-Applications cannot be found. Either the component that raises this event is not installed on your local computer or the installation is corrupted. You can install or repair the component on the local computer.`  
>   
>  如果遇到此错误，请单击**刷新**操作窗格中。 事件现在应能正确解码。  
  
> [!IMPORTANT]
>  您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目录不存在，请转到[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 示例](https://go.microsoft.com/fwlink/?LinkId=150780)若要下载所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。 此示例位于以下目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\ExtractWfData`  
  
## <a name="see-also"></a>请参阅  
 [AppFabric 监视示例](https://go.microsoft.com/fwlink/?LinkId=193959)
