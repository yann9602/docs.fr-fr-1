---
title: "Désactiver RealTimeStylus pour les applications WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 01a4d8f6d98eb341021442d9b7964816dd673374
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>Désactiver RealTimeStylus pour les applications WPF
Prise en charge pour le traitement d’entrée tactile Windows 7 intégrée Windows Presentation Foundation (WPF). La prise en charge est fournie via l’entrée de stylet en temps réel de la plateforme tablet en tant que <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, et <xref:System.Windows.UIElement.OnStylusMove%2A> événements. Windows 7 fournit également une entrée tactile en tant que messages de fenêtre WM_TOUCH Win32. Ces deux API s’excluent mutuellement sur le même HWND. Permettre l’entrée tactile via la plateforme Tablet PC (la valeur par défaut pour les applications WPF) désactive WM_TOUCH messages. Par conséquent, pour utiliser WM_TOUCH pour recevoir des messages de contact à partir d’une fenêtre WPF, vous devez désactiver la prise en charge intégrée de stylet dans WPF. Cela s’applique dans un scénario comme une fenêtre WPF hébergeant un composant qui utilise WM_TOUCH.  
  
 Pour désactiver WPF à l’écoute de l’entrée du stylet, supprimez tout tablet prend désormais en charge par la fenêtre WPF.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment supprimer la prise en charge de la plateforme de la tablette par défaut en utilisant la réflexion.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Interception d'entrée à partir du stylet](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md)
