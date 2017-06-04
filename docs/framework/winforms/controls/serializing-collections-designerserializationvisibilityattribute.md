---
title: "Proc&#233;dure pas &#224; pas&#160;: s&#233;rialisation des collections de types standard avec DesignerSerializationVisibilityAttribute | Microsoft Docs"
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
  - "collections, sérialisation"
  - "collections, types standard"
  - "DesiginerSerializationVisibilityAttribute (classe)"
  - "sérialisation, collections"
  - "types standard, collections"
ms.assetid: 020c9df4-fdc5-4dae-815a-963ecae5668c
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Proc&#233;dure pas &#224; pas&#160;: s&#233;rialisation des collections de types standard avec DesignerSerializationVisibilityAttribute
Vos contrôles personnalisés exposeront quelquefois une collection en tant que propriété.  Cette procédure pas à pas montre comment utiliser la classe <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> pour contrôler la façon dont une collection est sérialisée au moment du design.  L'application de la valeur <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> à votre propriété de collection garantit la sérialisation de la propriété.  
  
 Pour copier le code dans cette rubrique sous forme de liste unique, consultez [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](../Topic/How%20to:%20Serialize%20Collections%20of%20Standard%20Types%20with%20the%20DesignerSerializationVisibilityAttribute.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Avoir des autorisations suffisantes pour être en mesure de créer et d'exécuter des projets d'application Windows Forms sur l'ordinateur où Visual Studio est installé.  
  
## Création d'un contrôle qui a une collection sérialisable  
 La première étape consiste à créer un contrôle qui a une collection sérialisable en tant que propriété.  Vous pouvez modifier le contenu de cette collection à l'aide de l'**éditeur de collections** auquel vous pouvez accéder à partir de la fenêtre **Propriétés**.  
  
#### Pour créer un contrôle avec une collection sérialisable  
  
1.  Créez un projet de bibliothèque de contrôles Windows appelé `SerializationDemoControlLib`.  Pour plus d'informations, consultez [Windows Control Library Template](http://msdn.microsoft.com/fr-fr/722f4e2d-1310-4ed5-8f33-593337ab66b4).  
  
2.  Renommez `UserControl1` à `SerializationDemoControl`.  Pour plus d'informations, consultez [How to: Rename Identifiers](http://msdn.microsoft.com/fr-fr/2430f732-2b70-4516-8cf6-a7bb71cc9724).  
  
3.  Dans la fenêtre **Propriétés**, affectez à la propriété <xref:System.Windows.Forms.Padding.All%2A?displayProperty=fullName> la valeur `10`.  
  
4.  Placez un contrôle <xref:System.Windows.Forms.TextBox> dans le `SerializationDemoControl`.  
  
5.  Sélectionnez le contrôle <xref:System.Windows.Forms.TextBox>.  Dans la fenêtre **Propriétés**, définissez les propriétés suivantes.  
  
    |Propriété|Remplacez par|  
    |---------------|-------------------|  
    |**Multiline**|`true`|  
    |**Dock**|<xref:System.Windows.Forms.DockStyle>|  
    |**ScrollBars**|<xref:System.Windows.Forms.ScrollBars>|  
    |**ReadOnly**|`true`|  
  
6.  Dans l'**éditeur de code**, déclarez un champ de tableau de chaînes nommé `stringsValue` dans `SerializationDemoControl`.  
  
     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]  
  
7.  Définissez la propriété `Strings` sur le `SerializationDemoControl`.  
  
> [!NOTE]
>  La valeur <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> est utilisée pour activer la sérialisation de la collection.  
  
 [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
 [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
 [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]  
  
1.  Appuyez sur F5 pour générer le projet et exécuter votre contrôle dans le **conteneur de test UserControl**.  
  
2.  Recherchez la propriété `Strings` dans <xref:System.Windows.Forms.PropertyGrid> de l'élément **conteneur de test UserControl**.  Cliquez sur la propriété `Strings`, puis sur le bouton de sélection \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) pour ouvrir l'**éditeur de collections String**.  
  
3.  Entrez plusieurs chaînes dans l'**éditeur de collections String**.  Séparez\-les en appuyant sur la touche ENTRÉE à la fin de chaque chaîne.  Cliquez sur **OK** lorsque vous avez terminé d'ajouter des chaînes.  
  
> [!NOTE]
>  Les chaînes que vous avez tapées apparaissent dans le <xref:System.Windows.Forms.TextBox> du `SerializationDemoControl`.  
  
## Sérialisation d'une propriété de collection  
 Pour tester le comportement de sérialisation de votre contrôle, vous le placerez sur un formulaire et modifierez le contenu de la collection à l'aide de l'**éditeur de collections**.  Vous pouvez consulter l'état de collection sérialisée en examinant un fichier de concepteur spécial dans lequel le **Concepteur Windows Forms Designer** émet le code.  
  
#### Pour sérialiser une collection  
  
1.  Ajoutez un nouveau projet Application Windows à la solution.  Nommez le projet `SerializationDemoControlTest`.  
  
2.  Dans la **Boîte à outils**, recherchez l'onglet nommé **Composants SerializationDemoControlLib**.  Sous cet onglet, vous trouverez le `SerializationDemoControl`.  Pour plus d'informations, consultez [Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
3.  Ajoutez un `SerializationDemoControl` sur votre formulaire.  
  
4.  Recherchez la propriété `Strings` dans la fenêtre **Propriétés**.  Cliquez sur la propriété `Strings`, puis sur le bouton de sélection \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) pour ouvrir l'**éditeur de collections String**.  
  
5.  Entrez plusieurs chaînes dans l'**éditeur de collections String**.  Séparez\-les en appuyant sur la touche ENTRÉE à la fin de chaque chaîne.  Cliquez sur **OK** lorsque vous avez terminé d'ajouter des chaînes.  
  
> [!NOTE]
>  Les chaînes que vous avez tapées apparaissent dans le <xref:System.Windows.Forms.TextBox> du `SerializationDemoControl`.  
  
1.  Dans l'**Explorateur de solutions**, cliquez sur le bouton **Afficher tous les fichiers**.  
  
2.  Ouvrez le nœud **Form1**.  Vous trouverez en dessous un fichier appelé **Form1.Designer.cs** ou **Form1.Designer.vb**.  C'est le fichier dans lequel le **Concepteur Windows Forms** émet le code qui représente l'état au moment du design de votre formulaire et ses contrôles enfants.  Ouvrez ce fichier dans l'**éditeur de code**.  
  
3.  Ouvrez la région appelée **Code généré par le Concepteur Windows Form** et recherchez la section étiquetée **serializationDemoControl1**.  Sous cette étiquette se trouve le code qui représente l'état sérialisé de votre contrôle.  Les chaînes que vous avez entrées à l'étape 5 apparaissent dans une assignation à la propriété `Strings`.  L'exemple de code suivant affiche un code similaire à celui que vous verrez si vous tapez les chaînes « rouge », « orange » et « jaune ».  
  
4.  \[Visual Basic\]  
  
    ```  
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}  
    ```  
  
5.  \[C\#\]  
  
    ```  
    this.serializationDemoControl1.Strings = new string[] {  
            "red",  
            "orange",  
            "yellow"};  
    ```  
  
6.  Dans l'**éditeur de code**, remplacez la valeur de l'<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> de la propriété `Strings` par <xref:System.ComponentModel.DesignerSerializationVisibility>.  
  
7.  \[Visual Basic\]  
  
    ```  
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _  
    ```  
  
8.  \[C\#\]  
  
    ```  
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]  
    ```  
  
9. Régénérez la solution et répétez les étapes 4 à 8.  
  
> [!NOTE]
>  Dans ce cas, le **Concepteur Windows Forms** n'émet aucune assignation à la propriété `Strings`.  
  
## Étapes suivantes  
 Une fois que vous savez comment sérialiser une collection de types standard, pensez à intégrer plus profondément vos contrôles personnalisés dans l'environnement au moment du design.  Les rubriques suivantes décrivent comment améliorer l'intégration au moment du design de vos contrôles personnalisés :  
  
-   [Design\-Time Architecture](../Topic/Design-Time%20Architecture.md)  
  
-   [Attributs dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
  
-   [Designer Serialization Overview](../Topic/Designer%20Serialization%20Overview.md)  
  
-   [Procédure pas à pas : création d'un contrôle Windows Forms qui tire parti des fonctionnalités au moment du design de Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
  
## Voir aussi  
 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>   
 [Designer Serialization Overview](../Topic/Designer%20Serialization%20Overview.md)   
 [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](../Topic/How%20to:%20Serialize%20Collections%20of%20Standard%20Types%20with%20the%20DesignerSerializationVisibilityAttribute.md)   
 [Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)