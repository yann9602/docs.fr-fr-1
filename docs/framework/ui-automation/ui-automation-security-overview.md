---
title: "UI Automation Security Overview | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "UI Automation, security model"
  - "security model, UI Automation"
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
caps.latest.revision: 23
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 23
---
# UI Automation Security Overview
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette vue d'ensemble décrit le modèle de sécurité pour [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] dans [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].  
  
<a name="User_Account_Control"></a>   
## Contrôle de compte d'utilisateur  
 La sécurité est un objectif majeur de [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)]. Parmi les innovations apportées, citons pour les utilisateurs la possibilité d'exécuter le système d'exploitation sous un compte d'utilisateur standard \(non\-administrateur\) sans être forcément bloqués par des applications et des services en cours d'exécution qui nécessitent des privilèges plus élevés.  
  
 Dans [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], la plupart des applications sont fournies avec un jeton standard ou administratif. Si une application ne peut pas être identifiée en tant qu'application administrative, elle est lancée par défaut en tant qu'application standard. Avant le lancement d'une application identifiée en tant qu'application administrative, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] invite l'utilisateur à consentir l'exécution de l'application avec des privilèges élevés. L'invite de consentement s'affiche par défaut, même si l'utilisateur est membre du groupe Administrateurs local. Cela est dû au fait que les administrateurs sont considérés comme des utilisateurs standard jusqu'à ce qu'une application ou un composant système nécessitant des informations d'identification d'administration demande l'autorisation de s'exécuter.  
  
<a name="Tasks_Requiring_Higher_Privileges"></a>   
## Tâches nécessitant des privilèges plus élevés  
 Quand un utilisateur tente d'effectuer une tâche qui nécessite des privilèges d'administrateur, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] affiche une boîte de dialogue qui invite l'utilisateur à donner son consentement pour continuer. Cette boîte de dialogue bénéficie d'une protection contre les communications interprocessus, ce qui empêche les logiciels malveillants de simuler l'entrée de l'utilisateur. De même, d'autres processus ne sont normalement pas autorisés à accéder à l'écran d'ouverture de session sur le Bureau.  
  
 Les clients UI Automation doivent communiquer avec d’autres processus, certains d’entre eux pouvant être exécutés à un niveau de privilège supérieur. Les clients peuvent aussi avoir besoin d'accéder à des boîtes de dialogue système qui ne sont normalement pas visibles à d'autres processus. Par conséquent, les clients [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] doivent être approuvés par le système et s'exécuter avec des privilèges spéciaux.  
  
 Pour avoir l'autorisation de communiquer avec des applications exécutées à un niveau de privilège plus élevé, les applications doivent être signées.  
  
<a name="Manifest_Files"></a>   
## Fichiers manifeste  
 Pour accéder à l'[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] du système protégé, les applications doivent être générées avec un fichier manifeste contenant un attribut spécial. Cet attribut `uiAccess` est inclus dans la balise `requestedExecutionLevel`, comme suit :  
  
 `<trustInfo xmlns="urn:0073chemas-microsoft-com:asm.v3">`  
  
 `<security>`  
  
 `<requestedPrivileges>`  
  
 `<requestedExecutionLevel`  
  
 `level="highestAvailable"`  
  
 `UIAccess="true" />`  
  
 `</requestedPrivileges>`  
  
 `</security>`  
  
 `</trustInfo>`  
  
 Dans ce code, la valeur de l'attribut `level` n'est qu'un exemple.  
  
 `UIAccess` a la valeur « false » par défaut ; autrement dit, si l'attribut est omis ou qu'il n'existe aucun manifeste pour l'assembly, l'application ne pourra pas accéder à l'[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] protégée.  
  
 Pour plus d’informations sur la sécurité de [!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)], la signature des applications et la création de manifestes d’assembly, consultez la page décrivant les meilleures pratiques et recommandations à l’intention des développeurs pour les applications situées dans un environnement basé sur le principe des privilèges minimum, sur [MSDN](http://msdn.microsoft.com/library/default.asp?url=/library/dnlong/html/AccProtVista.asp).