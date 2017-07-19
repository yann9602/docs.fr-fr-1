---
title: "Comment&#160;: afficher un contr&#244;le dans la bo&#238;te de dialogue Choisir des &#233;l&#233;ments de bo&#238;te &#224; outils | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "global assembly cache, boîte de dialogue Choisir des éléments de boîte à outils"
  - "AssemblyFoldersEx, boîte de dialogue Choisir des éléments de boîte à outils"
  - "contrôles, affichage dans la boîte de dialogue Choisir des éléments de boîte à outils"
  - "inscription des dossiers d’assembly, boîte de dialogue Choisir des éléments de boîte à outils"
  - "Choisir des éléments de boîte à outils (boîte de dialogue), affichage de contrôles"
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: afficher un contr&#244;le dans la bo&#238;te de dialogue Choisir des &#233;l&#233;ments de bo&#238;te &#224; outils
Lorsque vous développez et distribuez des contrôles, vous souhaiterez peut\-être que ces contrôles s'affichent dans la boîte de dialogue **Choisir des éléments de boîte à outils**, laquelle s'affiche lorsque vous cliquez avec le bouton droit sur la **boîte à outils** et que vous sélectionnez **Choisir les éléments**.  Vous pouvez autoriser votre contrôle à s'afficher dans cette boîte de dialogue à l'aide de la procédure d'inscription AssemblyFoldersEx.  
  
### Pour afficher votre contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils  
  
-   Installez votre assembly de contrôle dans le Global Assembly Cache.  Pour plus d'informations, consultez [Comment : installer un assembly dans le Global Assembly Cache](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md).  
  
     ou  
  
-   Enregistrez votre contrôle et ses assemblys au moment du design associés à l'aide de la procédure d'inscription AssemblyFoldersEx.  AssemblyFoldersEx est un emplacement de Registre où les fournisseurs tiers stockent des chemins d'accès pour chaque version de l'infrastructure qu'ils prennent en charge.  La résolution au moment du design peut utiliser cet emplacement de Registre pour rechercher des assemblys de référence.  Le script de registre peut spécifier les contrôles que vous souhaitez voir s'afficher dans la Boîte à outils.  Pour plus d'informations, consultez [Déploiement d'un contrôle personnalisé et d'assemblys au moment du design](http://msdn.microsoft.com/fr-fr/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).  
  
## Voir aussi  
 [Choose Toolbox Items Dialog Box \(Visual Studio\)](http://msdn.microsoft.com/fr-fr/bd07835f-18a8-433e-bccc-7141f65263bb)   
 [Déploiement d'un contrôle personnalisé et d'assemblys au moment du design](http://msdn.microsoft.com/fr-fr/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)   
 [Développement de contrôles Windows Forms au moment du design](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)   
 [Comment : installer un assembly dans le Global Assembly Cache](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)   
 [Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)