---
title: "Comment : verrouiller des contrôles sur des Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 30808d2102a1be41381f0e07c9f0f37bfb4a5a56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-lock-controls-to-windows-forms"></a>Comment : verrouiller des contrôles sur des Windows Forms
Lorsque vous concevez l’interface utilisateur (IU) de votre application Windows, vous pouvez verrouiller les contrôles une fois qu’ils sont correctement placés, afin que ne pas par inadvertance déplacer ou redimensionner les lors de la définition d’autres propriétés.  
  
 En outre, vous pouvez verrouiller et déverrouiller tous les contrôles sur le formulaire à la fois, ce qui est utile pour les formulaires avec de nombreux contrôles, ou vous pouvez déverrouiller des contrôles individuels. Une fois que vous avez placés tous les contrôles où vous le souhaitez dans le formulaire, les verrouiller tous les en place pour éviter des mouvements erronée.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-lock-a-control"></a>Pour verrouiller un contrôle  
  
1.  Dans le **propriétés** fenêtre, cliquez sur le **verrouillé** et sélectionnez `true`. (Double-cliquez sur le nom Active ou désactive le paramètre de propriété.)  
  
     Ou bien, cliquez sur le contrôle et choisissez **verrouiller les contrôles**.  
  
    > [!NOTE]
    >  Contrôles de verrouillage empêche les déplacé vers une nouvelle taille ou l’emplacement sur l’aire de conception. Toutefois, vous pouvez toujours modifier la taille ou l’emplacement des contrôles à l’aide de la **propriétés** fenêtre ou dans le code.  
  
### <a name="to-lock-all-the-controls-on-a-form"></a>Pour verrouiller tous les contrôles sur un formulaire  
  
1.  À partir de la **Format** menu, choisissez **verrouiller les contrôles**.  
  
    > [!NOTE]
    >  Cette commande verrouille la taille du formulaire, car un formulaire est un contrôle.  
  
### <a name="to-unlock-all-locked-controls-on-a-form"></a>Pour déverrouiller verrouillés tous les contrôles sur un formulaire  
  
1.  À partir de la **Format** menu, choisissez **verrouiller les contrôles**.  
  
     Tous les contrôles précédemment verrouillés du formulaire sont maintenant déverrouillé.  
  
### <a name="to-unlock-locked-controls-individually"></a>Pour déverrouiller les contrôles verrouillés individuellement  
  
1.  Dans le **propriétés** fenêtre, cliquez sur le **verrouillé** et sélectionnez `false`. (Double-cliquez sur le nom Active ou désactive le paramètre de propriété.)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Disposition des contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Classement par fonction des contrôles Windows Forms](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
