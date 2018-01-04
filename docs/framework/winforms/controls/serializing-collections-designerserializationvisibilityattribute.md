---
title: "Procédure pas à pas : sérialisation des collections de types standard avec DesignerSerializationVisibilityAttribute"
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
- serialization [Windows Forms], collections
- standard types [Windows Forms], collections
- collections [Windows Forms], serializing
- collections [Windows Forms], standard types
ms.assetid: 020c9df4-fdc5-4dae-815a-963ecae5668c
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 060f411dfc7c3153fdf0e0d6e19781f0d60b141b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-serializing-collections-of-standard-types-with-the-designerserializationvisibilityattribute"></a>Procédure pas à pas : sérialisation des collections de types standard avec DesignerSerializationVisibilityAttribute
Vos contrôles personnalisés parfois expose une collection en tant que propriété. Cette procédure pas à pas montre comment utiliser la <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> classe pour contrôler la façon dont une collection est sérialisée au moment du design. Appliquer le <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> valeur à votre propriété de collection garantit que la propriété est sérialisée.  
  
 Pour copier le code dans cette rubrique sous forme de liste unique, consultez [Comment : sérialiser des Collections de Types Standard avec DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   Autorisations suffisantes pour pouvoir créer et exécuter des projets d’application Windows Forms sur l’ordinateur où Visual Studio est installé.  
  
## <a name="creating-a-control-that-has-a-serializable-collection"></a>Création d’un contrôle qui a une Collection sérialisable  
 La première étape consiste à créer un contrôle qui a une collection sérialisable en tant que propriété. Vous pouvez modifier le contenu de cette collection à l’aide de la **éditeur de collections**, auquel vous pouvez accéder depuis la **propriétés** fenêtre.  
  
#### <a name="to-create-a-control-with-a-serializable-collection"></a>Pour créer un contrôle avec une collection sérialisable  
  
1.  Créez un projet de bibliothèque de contrôles Windows appelé `SerializationDemoControlLib`. Pour plus d’informations, consultez [modèle de bibliothèque de contrôles Windows](http://msdn.microsoft.com/en-us/722f4e2d-1310-4ed5-8f33-593337ab66b4).  
  
2.  Renommer `UserControl1` à `SerializationDemoControl`. Pour plus d’informations, consultez [Comment : renommer des identificateurs](http://msdn.microsoft.com/en-us/2430f732-2b70-4516-8cf6-a7bb71cc9724).  
  
3.  Dans le **propriétés** fenêtre, définissez la valeur de la <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> propriété `10`.  
  
4.  Place un <xref:System.Windows.Forms.TextBox> contrôler dans le `SerializationDemoControl`.  
  
5.  Sélectionnez le contrôle <xref:System.Windows.Forms.TextBox>. Dans le **propriétés** fenêtre, définissez les propriétés suivantes.  
  
    |Propriété|Remplacer par|  
    |--------------|---------------|  
    |**Multiline**|`true`|  
    |**Station d’accueil**|<xref:System.Windows.Forms.DockStyle.Fill>|  
    |**Barres de défilement**|<xref:System.Windows.Forms.ScrollBars.Vertical>|  
    |**ReadOnly**|`true`|  
  
6.  Dans le **éditeur de Code**, déclarez un champ de tableau de type chaîne nommé `stringsValue` dans `SerializationDemoControl`.  
  
     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]  
  
7.  Définir le `Strings` propriété sur le `SerializationDemoControl`.  
  
> [!NOTE]
>  Le <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> valeur est utilisée pour activer la sérialisation de la collection.  
  
 [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
 [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
 [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]  
  
1.  Appuyez sur F5 pour générer le projet et exécuter votre contrôle dans le **Conteneur de test UserControl**.  
  
2.  Rechercher les `Strings` propriété dans le <xref:System.Windows.Forms.PropertyGrid> de la **conteneur de Test UserControl**. Cliquez sur le `Strings` propriété, puis cliquez sur le bouton de sélection (![capture d’écran de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) pour ouvrir la **éditeur de Collection de chaînes**.  
  
3.  Entrez plusieurs chaînes dans le **éditeur de collections String**. Séparez-les en appuyant sur la touche entrée à la fin de chaque chaîne. Cliquez sur **OK** lorsque vous avez terminé d’entrer des chaînes.  
  
> [!NOTE]
>  Les chaînes que vous avez tapé s’affichent dans le <xref:System.Windows.Forms.TextBox> de la `SerializationDemoControl`.  
  
## <a name="serializing-a-collection-property"></a>Sérialisation d’une propriété de Collection  
 Pour tester le comportement de sérialisation de votre contrôle, vous allez placer sur un formulaire et modifier le contenu de la collection avec le **éditeur de collections**. Vous pouvez consulter l’état de collection sérialisée en examinant un fichier de concepteur spécial dans lequel le **Concepteur Windows Forms** émet du code.  
  
#### <a name="to-serialize-a-collection"></a>Pour sérialiser une collection  
  
1.  Ajouter un projet d’Application Windows à la solution. Attribuez un nom au projet `SerializationDemoControlTest`.  
  
2.  Dans le **boîte à outils**, recherchez l’onglet nommé **Composants SerializationDemoControlLib**. Dans cet onglet, vous trouverez le `SerializationDemoControl`. Pour plus d’informations, consultez l’article [Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
3.  Place un `SerializationDemoControl` sur votre formulaire.  
  
4.  Rechercher les `Strings` propriété dans le **propriétés** fenêtre. Cliquez sur le `Strings` propriété, puis cliquez sur le bouton de sélection (![capture d’écran de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) pour ouvrir la **éditeur de Collection de chaînes**.  
  
5.  Entrez plusieurs chaînes dans le **éditeur de collections String**. Séparez-les en appuyant sur la touche entrée à la fin de chaque chaîne. Cliquez sur **OK** lorsque vous avez terminé d’entrer des chaînes.  
  
> [!NOTE]
>  Les chaînes que vous avez tapé s’affichent dans le <xref:System.Windows.Forms.TextBox> de la `SerializationDemoControl`.  
  
1.  Dans l’**Explorateur de solutions**, cliquez sur le bouton **Afficher tous les fichiers**.  
  
2.  Ouvrez le **Form1** nœud. En dessous, il est un fichier appelé **Form1.Designer.cs** ou **Form1.Designer.vb**. Il s’agit du fichier dans lequel le **Concepteur Windows Forms** émet du code représentant l’état au moment du design de votre formulaire et ses contrôles enfants. Ouvrez ce fichier dans **l’éditeur de code**.  
  
3.  Ouvrez la région appelée **code généré par le Concepteur Windows Form** et recherchez la section intitulée **serializationDemoControl1**. Sous cette étiquette est le code qui représente l’état sérialisé de votre contrôle. Les chaînes que vous avez tapé à l’étape 5 apparaissent dans une assignation à la `Strings` propriété. Les exemples de code suivant en c# et Visual Basic, afficher le code similaire à ce que vous verrez si vous avez tapé les chaînes « rouge », « orange » et « jaune ».  
  
    ```csharp  
    this.serializationDemoControl1.Strings = new string[] {  
            "red",  
            "orange",  
            "yellow"};  
    ```  
    
    ```vb  
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}  
    ```
  
4.  Dans le **éditeur de Code**, modifiez la valeur de la <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> sur la `Strings` propriété <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.  
  
    ```csharp  
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]  
    ```  
    ```vb  
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _  
    ```  
  
5. Régénérez la solution et répétez les étapes 3 et 4.  
  
> [!NOTE]
>  Dans ce cas, le **Concepteur Windows Forms** n’émet aucune assignation à la `Strings` propriété.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Une fois que vous savez comment sérialiser une collection de types standard, intégrez vos contrôles personnalisés plus profondément dans l’environnement au moment du design. Les rubriques suivantes décrivent comment améliorer l’intégration au moment du design de vos contrôles personnalisés :  
  
-   [Architecture au moment du design](http://msdn.microsoft.com/library/4881917b-628f-4689-b872-472e4f8a4e3a)  
  
-   [Attributs dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
  
-   [Vue d’ensemble de la sérialisation du Concepteur](http://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
  
-   [Procédure pas à pas : création d’un contrôle Windows Forms qui tire parti des fonctionnalités au moment du design de Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>  
 [Vue d’ensemble de la sérialisation du Concepteur](http://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
 [Comment : sérialiser des Collections de Types Standard avec DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)  
 [Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
