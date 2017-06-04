---
title: "GetCustomUI | Microsoft Docs"
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
  - "messages d'erreur personnalisés (WPF)"
  - "GetCustomUI (méthode)"
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# GetCustomUI
Appelée par PresentationHost.exe pour obtenir des messages d'erreur et des messages d'avancement personnalisés provenant de l'hôte, s'il est implémenté.  
  
## Syntaxe  
  
```  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
#### Paramètres  
 `pwzProgressAssemblyName`  
  
 \[out\] Pointeur vers l'assembly qui contient l'interface utilisateur d'avancement fournie par l'hôte.  
  
 `pwzProgressClassName`  
  
 \[out\] Nom de la classe qui correspond à l'interface utilisateur d'avancement fournie par l'hôte, de préférence un fichier [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] avec <xref:System.Windows.Controls.Page> comme élément de niveau supérieur.  Cette classe réside dans l'assembly spécifié par `pwzProgressAssemblyName`.  
  
 `pwzErrorAssemblyName`  
  
 \[out\] Pointeur vers l'assembly qui contient l'interface utilisateur d'erreur fournie par l'hôte.  
  
 `pwzErrorClassName`  
  
 \[out\] Nom de la classe qui correspond à l'interface utilisateur d'erreur fournie par l'hôte, de préférence un fichier XAML avec <xref:System.Windows.Controls.Page> comme élément de niveau supérieur.  Cette classe réside dans l'assembly spécifié par `pwzErrorAssemblyName`.  
  
## Valeur de propriété\/valeur de retour  
 HRESULT : ignoré.  
  
## Notes  
 Une application hôte peut avoir un thème spécifique auquel les interfaces utilisateur par défaut de PresentationHost.exe ne sont peut\-être pas conformes.  Si tel est le cas, l'application hôte peut implémenter la méthode [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) pour retourner les interfaces utilisateur d'erreur et d'avancement à PresentationHost.exe.  PresentationHost.exe appelle toujours la méthode [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) avant d'utiliser ses interfaces utilisateur par défaut.  
  
 Cette fonction est appelée une fois pendant l'initialisation de PresentationHost.  
  
## Voir aussi  
 [IWpfHostSupport](../../../../docs/framework/wpf/app-development/iwpfhostsupport.md)