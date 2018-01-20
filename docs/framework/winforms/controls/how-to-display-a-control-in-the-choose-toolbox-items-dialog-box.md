---
title: "Comment : afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3964551ba2eec0980541e95a7db20ef057a1dd61
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Comment : afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils
Lorsque vous développez et distribuez des contrôles, vous pouvez que ces contrôles s’affichent dans le **choisir des éléments de boîte à outils** boîte de dialogue qui s’affiche lorsque vous cliquez sur le **boîte à outils** et sélectionnez  **Choisissez les éléments**. Vous pouvez activer votre contrôle s’affiche dans cette boîte de dialogue à l’aide de la procédure d’inscription AssemblyFoldersEx.  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a>Pour afficher votre contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils  
  
-   Installer votre assembly de contrôle dans le global assembly cache. Pour plus d’informations, consultez [Comment : installer un Assembly dans le Global Assembly Cache](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
  
     - ou -  
  
-   Inscrire votre contrôle et ses assemblys au moment du design associés à l’aide de la procédure d’inscription AssemblyFoldersEx. AssemblyFoldersEx est un emplacement de Registre dans lequel stockent les chemins d’accès pour chaque version de l’infrastructure qu’ils prennent en charge des fournisseurs tiers. Au moment du design résolution peut ressembler à cet emplacement de Registre pour rechercher des assemblys de référence. Le script de Registre peut spécifier les contrôles que vous souhaitez voir apparaître dans la boîte à outils. Pour plus d’informations, consultez [déploiement d’un contrôle personnalisé et des assemblys au moment du Design (Visual Studio 2013)](http://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).  
  
## <a name="see-also"></a>Voir aussi  
 [Choisir des éléments de boîte à outils, boîte de dialogue (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [Déploiement d’un contrôle personnalisé et des assemblys au moment du Design (Visual Studio 2013)](http://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)  
 [Développement de contrôles Windows Forms au moment du design](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [Guide pratique pour installer un assembly dans le Global Assembly Cache](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
