---
title: "Comment : détecter si le plug-in WPF de Firefox est installé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87e821bd95679372fd169b7880e969fd10b5d03c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>Comment : détecter si le plug-in WPF de Firefox est installé
Le [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] plug-in pour Firefox permet aux [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] et de perdre des fichiers XAML à exécuter dans le navigateur Mozilla Firefox. Cette rubrique fournit un script écrit en HTML et JavaScript, les administrateurs peuvent utiliser pour déterminer si le plug-in pour Firefox WPF est installé.  
  
> [!NOTE]
>  Pour plus d’informations sur l’installation, déploiement et la détection du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], consultez [installer le .NET Framework pour les développeurs](../../../../docs/framework/install/guide-for-developers.md).  
  
## <a name="example"></a>Exemple  
 Lorsque le [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] est installé, l’ordinateur client est configuré avec un plug-in WPF pour Firefox. L’exemple de script suivant vérifie le plug-in WPF pour Firefox, puis affiche un message d’état approprié.  
  
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
  
 Si la vérification pour le plug-in WPF pour Firefox est réussie, le message d’état suivant s’affiche :  
  
 `The WPF plug-in for Firefox is installed.`  
  
 Sinon, le message d’état suivant s’affiche :  
  
 `The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`  
  
## <a name="see-also"></a>Voir aussi  
 [Détecter si .NET Framework 3.0 est installé](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)  
 [Détecter si .NET Framework 3.5 est installé](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-5-is-installed.md)  
 [Vue d’ensemble des applications du navigateur XAML WPF](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)
