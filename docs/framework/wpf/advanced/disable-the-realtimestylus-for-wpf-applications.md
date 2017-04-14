---
title: "D&#233;sactiver RealTimeStylus pour les applications WPF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
caps.latest.revision: 3
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 3
---
# D&#233;sactiver RealTimeStylus pour les applications WPF
Windows Presentation Foundation \(WPF\) intègre la prise en charge du traitement de l'entrée tactile Windows 7. Cette prise en charge se fait par le biais de l'entrée de stylet en temps réel de la plateforme Tablet en tant qu'événements <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A> et <xref:System.Windows.UIElement.OnStylusMove%2A>.  Windows 7 fournit également une entrée tactile multipoint sous la forme de messages de fenêtre WM\_TOUCH Win32.  Ces deux API s'excluent mutuellement sur le même HWND.  Permettre l'entrée tactile via la plateforme de Tablet \(valeur par défaut pour les applications WPF\) entraîne la désactivation des messages WM\_TOUCH.  Par conséquent, pour utiliser WM\_TOUCH pour recevoir des messages de fonctions tactiles à partir d'une fenêtre WPF, vous devez désactiver la prise en charge du stylet intégré dans WPF.  C'est applicable dans un scénario tel qu'une fenêtre WPF hébergeant un composant qui utilise WM\_TOUCH.  
  
 Pour désactiver l'écoute WPF de l'entrée de stylet, supprimez toutes les prises en charge de Tablet ajoutées par la fenêtre WPF.  
  
## Exemple  
 L'exemple de code suivant indique comment supprimer la prise en charge de la plateforme de Tablet par défaut à l'aide de la réflexion.  
  
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
  
## Voir aussi  
 [Interception d'entrée à partir du stylet](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md)