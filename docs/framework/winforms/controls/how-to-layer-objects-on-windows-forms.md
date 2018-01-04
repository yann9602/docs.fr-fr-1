---
title: "Comment : superposer des objets dans les Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f042816b912a0de643dd1d0f66ddba6d5eff7df2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-layer-objects-on-windows-forms"></a>Comment : superposer des objets dans les Windows Forms
Lorsque vous créez une interface utilisateur complexe, ou utilisez un formulaire d’interface (multidocument MDI) document, vous souhaitez souvent superposer les contrôles et les formulaires enfants pour créer des interfaces utilisateur (IU) plus complexes. Pour déplacer et effectuer le suivi des contrôles et fenêtres dans le contexte d’un groupe, vous manipulez leur ordre de plan. *Ordre de plan* est la superposition visuelle des contrôles d’un formulaire sur l’axe z (profondeur). La fenêtre en haut de l’ordre de plan superpose à toutes les autres fenêtres. Toutes les autres fenêtres chevauchent la fenêtre en bas de l’ordre de plan.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-layer-controls-at-design-time"></a>Pour superposer des contrôles au moment du design  
  
1.  Sélectionnez un contrôle à la couche.  
  
2.  Sur le **Format** menu, pointez sur **commande**, puis cliquez sur **mettre au premier plan** ou **arrière-plan**.  
  
### <a name="to-layer-controls-programmatically"></a>Pour superposer les contrôles par programmation  
  
-   Utilisez le <xref:System.Windows.Forms.Control.BringToFront%2A> et <xref:System.Windows.Forms.Control.SendToBack%2A> méthodes permettant de manipuler l’ordre de plan des contrôles.  
  
     Par exemple, si un <xref:System.Windows.Forms.TextBox> contrôle, `txtFirstName`, est sous un autre contrôle et que vous souhaitez qu’il en haut, utilisez le code suivant :  
  
    ```vb  
    txtFirstName.BringToFront()  
    ```  
  
    ```csharp  
    txtFirstName.BringToFront();  
    ```  
  
    ```cpp  
    txtFirstName->BringToFront();  
    ```  
  
> [!NOTE]
>  Windows Forms prend en charge *contrôler la relation contenant-contenu*. Fonction consiste à placer un nombre de contrôles dans un contrôle conteneur, comme un nombre de <xref:System.Windows.Forms.RadioButton> des contrôles dans un <xref:System.Windows.Forms.GroupBox> contrôle. Vous pouvez ensuite superposer les contrôles dans le contrôle conteneur. La zone de groupe est déplacée, les contrôles, car elle contient.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Disposition des contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Classement par fonction des contrôles Windows Forms](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
