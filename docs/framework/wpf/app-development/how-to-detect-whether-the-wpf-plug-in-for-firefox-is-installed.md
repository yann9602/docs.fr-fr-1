---
title: "Comment&#160;: d&#233;tecter si le plug-in WPF de Firefox est install&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "vérifier le plug-in Firefox (WPF)"
  - "détecter l'installation de Firefox (WPF)"
  - "détecter si le plug-in WPF de Firefox est installé (WPF)"
  - "Firefox (WPF), détecter l'installation"
  - "plug-in de Firefox (WPF)"
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: d&#233;tecter si le plug-in WPF de Firefox est install&#233;
Le plug\-in [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] pour Firefox permet aux [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] et aux fichiers XAML libres de fonctionner dans le navigateur Mozilla Firefox.  Cette rubrique fournit un script écrit en HTML et JavaScript que les administrateurs peuvent utiliser pour déterminer si le plug\-in WPF pour Firefox est installé.  
  
> [!NOTE]
>  Pour plus d'informations sur l'installation, le déploiement et la détection du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], consultez [Installation du .NET Framework](../../../../docs/framework/install/guide-for-developers.md).  
  
## Exemple  
 Lorsque le [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] est installé, l'ordinateur client est configuré avec un plug\-in WPF pour Firefox.  L'exemple de script suivant recherche le plug\-in WPF pour Firefox, puis affiche un message d'état approprié.  
  
```  
<HTML>  
  
  <HEAD>  
    <TITLE>Test for the WPF plug-in for Firefox</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT type="text/javascript">  
    <!--  
    function OnLoad()  
    {  
  
       // Check for the WPF plug-in for Firefox and report  
       var msg = "The WPF plug-in for Firefox is ";  
       var wpfPlugin = navigator.plugins["Windows Presentation Foundation"];  
       if( wpfPlugin != null ) {  
          document.writeln(msg + " installed.");  
       }  
       else {  
          document.writeln(msg + " not installed. Please install or reinstall the .NET Framework 3.5.");  
       }  
    }  
    -->  
    </SCRIPT>  
  </HEAD>  
  
  <BODY onload="OnLoad()" />  
  
</HTML>  
```  
  
 Si le contrôle pour le plug\-in WPF pour Firefox est réussi, le message d'état suivant est affiché :  
  
 `The WPF plug-in for Firefox is installed.`  
  
 Sinon, le message d'état suivant apparaît :  
  
 `The WPF plug-in for Firefox is not installed.  Please install or reinstall the .NET Framework 3.5.`  
  
## Voir aussi  
 [Détecter si .NET Framework 3.0 est installé](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)   
 [Détecter si .NET Framework 3.5 est installé](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-5-is-installed.md)   
 [Vue d'ensemble des applications de navigateur XAML](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)