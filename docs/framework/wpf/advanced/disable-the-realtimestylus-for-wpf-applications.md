---
title: '禁用用于 WPF 应用程序的 RealTimeStylus '
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: e44b71ac5af64ab3a6cb008db71e5a8881592e91
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124678"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>禁用用于 WPF 应用程序的 RealTimeStylus 
Windows Presentation Foundation (WPF) 提供了内置支持来处理 Windows 7 触控输入。这种支持是通过为 tablet 平台的实时触笔输入<xref:System.Windows.UIElement.OnStylusDown%2A>， <xref:System.Windows.UIElement.OnStylusUp%2A>，和<xref:System.Windows.UIElement.OnStylusMove%2A>事件。 Windows 7 还提供了作为 Win32 WM_TOUCH 窗口消息的多点触控输入。 这两个 Api 上的同一个 HWND 互相排斥。 启用触控输入通过 tablet 平台 （WPF 应用程序的默认值） 禁用 WM_TOUCH 消息。 因此，若要使用 WM_TOUCH 从 WPF 窗口接收触控消息，则必须禁用在 WPF 中的内置触笔支持。 此选项适用于使用 WM_TOUCH 组件宿主的 WPF 窗口类似的情况。  
  
 若要禁用 WPF 笔针输入到侦听，删除了由 WPF 窗口添加任何平板电脑支持。  
  
## <a name="example"></a>示例  
 下面的示例代码演示如何使用反射删除默认 tablet 平台支持。  
  
```  
public static void DisableWPFTabletSupport()  
{  
    // Get a collection of the tablet devices for this window.    
    TabletDeviceCollection devices = System.Windows.Input.Tablet.TabletDevices;  
  
    if (devices.Count > 0)  
    {     
        // Get the Type of InputManager.  
        Type inputManagerType = typeof(System.Windows.Input.InputManager);  
  
        // Call the StylusLogic method on the InputManager.Current instance.  
        object stylusLogic = inputManagerType.InvokeMember("StylusLogic",  
                    BindingFlags.GetProperty | BindingFlags.Instance | BindingFlags.NonPublic,  
                    null, InputManager.Current, null);  
  
        if (stylusLogic != null)  
        {  
            //  Get the type of the stylusLogic returned from the call to StylusLogic.  
            Type stylusLogicType = stylusLogic.GetType();  
  
            // Loop until there are no more devices to remove.  
            while (devices.Count > 0)  
            {  
                // Remove the first tablet device in the devices collection.  
                stylusLogicType.InvokeMember("OnTabletRemoved",  
                        BindingFlags.InvokeMethod | BindingFlags.Instance | BindingFlags.NonPublic,  
                        null, stylusLogic, new object[] { (uint)0 });  
            }                  
        }  
  
    }  
}  
```  
  
## <a name="see-also"></a>请参阅

- [截获触笔输入](intercepting-input-from-the-stylus.md)
