---
title: "Proc&#233;dure pas &#224; pas&#160;: activation de la fonction glisser-d&#233;placer sur un contr&#244;le utilisateur | Microsoft Docs"
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
  - "glisser-déplacer (WPF), procédure pas à pas"
  - "procédure pas à pas (WPF), glisser et déposer"
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Proc&#233;dure pas &#224; pas&#160;: activation de la fonction glisser-d&#233;placer sur un contr&#244;le utilisateur
Cette procédure pas à pas explique comment créer un contrôle utilisateur personnalisé qui peut participer au transfert de données par glisser\-déplacer dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 Dans cette procédure pas à pas, vous allez créer un <xref:System.Windows.Controls.UserControl> WPF personnalisé qui représente une forme de cercle.  Vous implémenterez la fonctionnalité sur le contrôle afin d'activer le transfert de données par glisser\-déplacer.  Par exemple, si vous faites glisser les données d'un contrôle Circle à un autre, les données de couleur de remplissage sont copiées du cercle source au cercle cible.  Si vous faites glisser un contrôle Circle vers <xref:System.Windows.Controls.TextBox>, la représentation sous forme de chaîne de la couleur de remplissage est copiée dans <xref:System.Windows.Controls.TextBox>.  Vous créerez également une petite application qui contient deux contrôles Panel et un <xref:System.Windows.Controls.TextBox> pour tester la fonctionnalité de glisser\-déplacer.  Vous écrirez un code qui active les panneaux qui permettent de traiter les données Circle supprimées, ce qui vous permettra de déplacer ou de copier des éléments Circle de la collection Children d'un panneau à l'autre.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Créer un contrôle utilisateur personnalisé.  
  
-   Activer le contrôle utilisateur comme source de glissement.  
  
-   Activer le contrôle utilisateur comme cible de déplacement.  
  
-   Activer un panneau pour recevoir les données supprimées du contrôle utilisateur.  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Visual Studio 2010  
  
## Création du projet d'application  
 De cette section, vous créerez l'infrastructure d'application, qui comprend une page principale avec deux panneaux et un <xref:System.Windows.Controls.TextBox>.  
  
### Pour créer le projet  
  
1.  Créez un projet d'application WPF en Visual Basic ou Visual C\# nommé `DragDropExample`.  Pour plus d'informations, consultez [Comment : créer un projet d'application WPF](http://msdn.microsoft.com/fr-fr/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
2.  Ouvrez MainWindow.xaml.  
  
3.  Entre les balises <xref:System.Windows.Controls.Grid> ouvrante et fermante, ajoutez le balisage suivant.  
  
     Ce balisage crée l'interface utilisateur pour l'application de test.  
  
     [!code-xml[DragDropWalkthrough#PanelsStep1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]  
  
## Ajout d'un nouveau contrôle utilisateur au projet  
 De cette section, vous allez ajouter un nouveau contrôle utilisateur au projet.  
  
### Pour ajouter un nouveau contrôle utilisateur  
  
1.  Dans le menu Projet, sélectionnez **Ajouter un contrôle utilisateur**.  
  
2.  Dans la boîte de dialogue Ajouter un nouvel élément, remplacez le nom `Circle.xaml`, et cliquez sur **Ajouter**.  
  
     Circle.xaml et son fichier code\-behind sont ajoutés au projet.  
  
3.  Ouvrez Circle.xaml.  
  
     Ce fichier contiendra les éléments de l'interface utilisateur du contrôle utilisateur.  
  
4.  Ajoutez le balisage suivant au <xref:System.Windows.Controls.Grid> racine pour créer un contrôle utilisateur simple qui présente un cercle bleu comme interface utilisateur.  
  
     [!code-xml[DragDropWalkthrough#EllipseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]  
  
5.  Ouvrez Circle.xaml.cs ou Circle.xaml.vb.  
  
6.  En C\#, ajoutez le code suivant après le constructeur par défaut pour créer un constructeur de copie.  En Visual Basic, ajoutez le code suivant pour créer un constructeur par défaut et un constructeur de copie.  
  
     Afin de pouvoir copier le contrôle utilisateur, ajoutez une méthode de constructeur de copie dans le fichier code\-behind.  Dans le contrôle utilisateur Circle simplifié, copiez uniquement le remplissage et la taille du contrôle utilisateur.  
  
     [!code-csharp[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]  
  
### Pour ajouter le contrôle utilisateur à la fenêtre principale  
  
1.  Ouvrez MainWindow.xaml.  
  
2.  Ajoutez le code XAML suivant dans la balise <xref:System.Windows.Window> d'ouverture pour créer une référence d'espace de noms XML à l'application actuelle.  
  
    ```  
    xmlns:local="clr-namespace:DragDropExample"  
    ```  
  
3.  Dans le premier <xref:System.Windows.Controls.StackPanel>, ajoutez le code XAML suivant pour créer deux instances du contrôle utilisateur Circle au premier panneau.  
  
     [!code-xml[DragDropWalkthrough#CirclesXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]  
  
     Le code XAML complet pour le panneau ressemble au code ci\-dessous.  
  
     [!code-xml[DragDropWalkthrough#PanelsStep2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]  
  
## Implémentation des événements de source de glissement dans le contrôle utilisateur  
 De cette section, vous substituerez la méthode <xref:System.Windows.UIElement.OnMouseMove%2A> et initialiserez l'opération de glisser\-déplacer.  
  
 Si une opération de glisser est démarrée \(le bouton de la souris est enfoncé et le pointeur est déplacé\), vous créez un package des données à transférer dans <xref:System.Windows.DataObject>.  Dans ce cas, le contrôle Circle place dans un package trois éléments de données, une représentation sous forme de chaîne de sa couleur de remplissage, une double représentation de sa hauteur et une copie de lui\-même.  
  
### Pour démarrer une opération de glisser\-déplacer  
  
1.  Ouvrez Circle.xaml.cs ou Circle.xaml.vb.  
  
2.  Ajoutez la substitution <xref:System.Windows.UIElement.OnMouseMove%2A> suivante pour fournir la gestion de classe pour l'événement <xref:System.Windows.UIElement.MouseMove>.  
  
     [!code-csharp[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]  
  
     Cette substitution <xref:System.Windows.UIElement.OnMouseMove%2A> exécute les tâches suivantes :  
  
    -   Vérifie si le bouton gauche de la souris est enfoncé alors que la souris se déplace.  
  
    -   Empaquète les données Circle dans un <xref:System.Windows.DataObject>.  Dans ce cas, le contrôle Circle place dans un package trois éléments de données, une représentation sous forme de chaîne de sa couleur de remplissage, une double représentation de sa hauteur et une copie de lui\-même.  
  
    -   Appelle la méthode <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=fullName> statique pour démarrer l'opération de glisser\-déplacer.  Passez les trois paramètres suivants à la méthode <xref:System.Windows.DragDrop.DoDragDrop%2A> :  
  
        -   `dragSource` : référence à ce contrôle.  
  
        -   `data` : <xref:System.Windows.DataObject> créé dans le code précédent.  
  
        -   `allowedEffects` : opérations de glisser\-déplacer autorisées, qui sont <xref:System.Windows.DragDropEffects> ou <xref:System.Windows.DragDropEffects>.  
  
3.  Appuyez sur F5 pour générer et exécuter l'application.  
  
4.  Cliquez sur l'un des contrôles Circle et faites\-le glisser sur les panneaux, l'autre contrôle Circle et <xref:System.Windows.Controls.TextBox>.  Lorsque le glissement passe au\-dessus de <xref:System.Windows.Controls.TextBox>, le curseur change pour indiquer un déplacement.  
  
5.  Tout en faisant glisser un contrôle Circle au\-dessus de <xref:System.Windows.Controls.TextBox>, appuyez sur la touche CTRL.  Remarquez la façon dont le curseur change pour indiquer une copie.  
  
6.  Faites glisser\-déplacer un contrôle Circle sur <xref:System.Windows.Controls.TextBox>.  La représentation sous forme de chaîne de la couleur de remplissage du contrôle Circle est ajoutée à <xref:System.Windows.Controls.TextBox>.  
  
     ![Représentation sous forme de chaîne de la couleur de remplissage du cercle](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop\_ColorString")  
  
 Par défaut, le curseur change pendant une opération de glisser\-déplacer pour montrer le résultat du déplacement des données.  Vous pouvez personnaliser les commentaires donnés à l'utilisateur en gérant l'événement <xref:System.Windows.UIElement.GiveFeedback> et en définissant un autre curseur.  
  
### Pour fournir des commentaires à l'utilisateur  
  
1.  Ouvrez Circle.xaml.cs ou Circle.xaml.vb.  
  
2.  Ajoutez la substitution <xref:System.Windows.UIElement.OnGiveFeedback%2A> suivante pour fournir la gestion de classe pour l'événement <xref:System.Windows.UIElement.GiveFeedback>.  
  
     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]  
  
     Cette substitution <xref:System.Windows.UIElement.OnGiveFeedback%2A> exécute les tâches suivantes :  
  
    -   Vérifie que les valeurs <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> sont définies dans le gestionnaire d'événements <xref:System.Windows.UIElement.DragOver> de la cible du déplacement.  
  
    -   Définit un curseur personnalisé en fonction de la valeur <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A>.  Le curseur est conçu pour fourni un commentaire visuel à l'utilisateur sur le résultat du déplacement des données.  
  
3.  Appuyez sur F5 pour générer et exécuter l'application.  
  
4.  Faites glisser l'un des contrôles Circle sur les panneaux, l'autre contrôle Circle et <xref:System.Windows.Controls.TextBox>.  Remarquez que les curseurs sont à présent les curseurs personnalisés que vous avez spécifiés en substituant <xref:System.Windows.UIElement.OnGiveFeedback%2A>.  
  
     ![Glisser&#45;déplacer avec des curseurs personnalisés](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop\_CustomCursor")  
  
5.  Sélectionnez le mot `green` dans <xref:System.Windows.Controls.TextBox>.  
  
6.  Faites glisser le mot `green` sur un contrôle Circle.  Remarquez que les curseurs par défaut s'affichent pour montrer le résultat de l'opération de glisser\-déplacer.  Le curseur de commentaire est toujours défini par la source du glissement.  
  
## Implémentation des événements de cible de déplacement dans le contrôle utilisateur  
 De cette section, vous allez indiquer que le contrôle utilisateur est une cible de déplacement, substituez les méthodes qui permettent au contrôle utilisateur d'être une cible de déplacement et traiter l'élément qui y sont déposées.  
  
### Pour activer le contrôle utilisateur comme cible de déplacement.  
  
1.  Ouvrez Circle.xaml.  
  
2.  Dans la balise d'ouverture <xref:System.Windows.Controls.UserControl>, ajoutez la propriété <xref:System.Windows.UIElement.AllowDrop%2A> et affectez\-lui la valeur `true`.  
  
     [!code-xml[DragDropWalkthrough#UCTagXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]  
  
 La méthode <xref:System.Windows.UIElement.OnDrop%2A> est appelée lorsque la propriété <xref:System.Windows.UIElement.AllowDrop%2A> est définie à `true` et que les données de la source de glissement sont déposées sur le contrôle utilisateur Circle.  Dans cette méthode, vous allez traiter les données déplacées et appliquer les données au contrôle Circle.  
  
### Pour traiter les données déplacées  
  
1.  Ouvrez Circle.xaml.cs ou Circle.xaml.vb.  
  
2.  Ajoutez la substitution <xref:System.Windows.UIElement.OnDrop%2A> suivante pour fournir la gestion de classe pour l'événement <xref:System.Windows.UIElement.Drop>.  
  
     [!code-csharp[DragDropWalkthrough#OnDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]  
  
     Cette substitution <xref:System.Windows.UIElement.OnDrop%2A> exécute les tâches suivantes :  
  
    -   Utilise la méthode <xref:System.Windows.DataObject.GetDataPresent%2A> pour vérifier si les données glissées contiennent un objet String.  
  
    -   Utilise la méthode <xref:System.Windows.DataObject.GetData%2A> pour extraire des données de chaîne, le cas échéant.  
  
    -   Utilise <xref:System.Windows.Media.BrushConverter> pour essayer de convertir la chaîne en <xref:System.Windows.Media.Brush>.  
  
    -   Si la conversion réussit, applique le pinceau au <xref:System.Windows.Shapes.Shape.Fill%2A> de <xref:System.Windows.Shapes.Ellipse> qui fournit l'interface utilisateur du contrôle Circle.  
  
    -   Marque l'événement <xref:System.Windows.UIElement.Drop> comme étant géré.  Vous devez marquer l'événement de déplacer comme géré afin que les autres éléments qui reçoivent cet événement sachent que le contrôle utilisateur Circle l'a traité.  
  
3.  Appuyez sur F5 pour générer et exécuter l'application.  
  
4.  Sélectionnez le mot `green` dans <xref:System.Windows.Controls.TextBox>.  
  
5.  Faites glisser le texte vers un contrôle Circle et déposez\-le.  Le contrôle Circle passe du bleu au vert.  
  
     ![Convertir une chaîne en pinceau](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop\_DropGreenText")  
  
6.  Tapez le mot `green` dans <xref:System.Windows.Controls.TextBox>.  
  
7.  Sélectionnez le mot `gre` dans <xref:System.Windows.Controls.TextBox>.  
  
8.  Faites\-le glisser sur un contrôle Circle et déposez\-le.  Notez que le curseur change pour indiquer que le déplacement est autorisé, mais la couleur du contrôle Circle ne change pas car `gre` n'est pas une couleur valide.  
  
9. Effectuez l'opération de glisser\-déplacer du contrôle Circle vert vers le contrôle Circle bleu.  Le contrôle Circle passe du bleu au vert.  Notez que le curseur qui s'affiche dépend de la source du déplacement, <xref:System.Windows.Controls.TextBox> ou le contrôle Circle.  
  
 La définition de la propriété <xref:System.Windows.UIElement.AllowDrop%2A> à `true` et le traitement des données déposées sont les seules opérations requises pour autoriser un élément à devenir cible de l'opération de déplacer.  Toutefois, pour fournir une meilleure expérience utilisateur, vous devez également gérer les événements <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave> et <xref:System.Windows.UIElement.DragOver>.  Dans ces événements, vous pouvez exécuter des contrôles et fournir des commentaires supplémentaires à l'utilisateur avant que les données ne soient déplacées.  
  
 Lorsque les données sont glissées sur le contrôle utilisateur Circle, le contrôle doit indiquer à la source du glissement s'il peut traiter les données glissées.  Si le contrôle n'est pas capable de traiter les données, il doit refuser le déplacement.  Pour ce faire, vous allez gérer l'événement <xref:System.Windows.UIElement.DragOver> et définir la propriété <xref:System.Windows.DragEventArgs.Effects%2A>.  
  
### Pour vérifier que le déplacement de données est autorisé  
  
1.  Ouvrez Circle.xaml.cs ou Circle.xaml.vb.  
  
2.  Ajoutez la substitution <xref:System.Windows.UIElement.OnDragOver%2A> suivante pour fournir la gestion de classe pour l'événement <xref:System.Windows.UIElement.DragOver>.  
  
     [!code-csharp[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]  
  
     Cette substitution <xref:System.Windows.UIElement.OnDragOver%2A> exécute les tâches suivantes :  
  
    -   Affecte la valeur <xref:System.Windows.DragDropEffects> à la propriété <xref:System.Windows.DragEventArgs.Effects%2A>.  
  
    -   Exécute les mêmes vérifications que celles exécutées dans la méthode <xref:System.Windows.UIElement.OnDrop%2A> pour déterminer si le contrôle utilisateur Circle peut traiter les données glissées.  
  
    -   Si le contrôle utilisateur peut traiter les données, définit la propriété <xref:System.Windows.DragEventArgs.Effects%2A> sur <xref:System.Windows.DragDropEffects> ou <xref:System.Windows.DragDropEffects>.  
  
3.  Appuyez sur F5 pour générer et exécuter l'application.  
  
4.  Sélectionnez le mot `gre` dans <xref:System.Windows.Controls.TextBox>.  
  
5.  Faites glisser le texte vers un contrôle Circle.  Notez que le curseur change à présent pour indiquer que le déplacement n'est pas autorisé car `gre` n'est pas une couleur valide.  
  
 Vous pouvez améliorer encore plus l'expérience utilisateur en appliquant une vue d'ensemble de l'opération de déplacement.  Pour le contrôle utilisateur Circle, vous allez substituer les méthodes <xref:System.Windows.UIElement.OnDragEnter%2A> et <xref:System.Windows.UIElement.OnDragLeave%2A>.  Lorsque les données sont déplacées au\-dessus du contrôle, le <xref:System.Windows.Shapes.Shape.Fill%2A> de l'arrière\-plan actif est enregistré dans une variable d'espace réservé.  La chaîne est ensuite convertie en pinceau et appliquée au <xref:System.Windows.Shapes.Ellipse> qui fournit l'interface utilisateur du contrôle Circle.  Si les données sont glissées en dehors du contrôle Circle sans être déposées, la valeur <xref:System.Windows.Shapes.Shape.Fill%2A> d'origine est réappliquée au contrôle Circle.  
  
### Pour afficher un aperçu du résultat de l'opération de glisser\-déplacer  
  
1.  Ouvrez Circle.xaml.cs ou Circle.xaml.vb.  
  
2.  Dans la classe Circle, déclarez une variable <xref:System.Windows.Media.Brush> privée nommée `_previousFill` et initialisez\-la à `null`.  
  
     [!code-csharp[DragDropWalkthrough#Brush](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]  
  
3.  Ajoutez la substitution <xref:System.Windows.UIElement.OnDragEnter%2A> suivante pour fournir la gestion de classe pour l'événement <xref:System.Windows.UIElement.DragEnter>.  
  
     [!code-csharp[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]  
  
     Cette substitution <xref:System.Windows.UIElement.OnDragEnter%2A> exécute les tâches suivantes :  
  
    -   Enregistre la propriété <xref:System.Windows.Shapes.Shape.Fill%2A> de <xref:System.Windows.Shapes.Ellipse> dans la variable `_previousFill`.  
  
    -   Exécute les mêmes vérifications que celles exécutées dans la méthode <xref:System.Windows.UIElement.OnDrop%2A> pour déterminer si les données peuvent être converties en <xref:System.Windows.Media.Brush>.  
  
    -   Si les données sont converties est en <xref:System.Windows.Media.Brush> valide, applique le <xref:System.Windows.Shapes.Shape.Fill%2A> de <xref:System.Windows.Shapes.Ellipse>.  
  
4.  Ajoutez la substitution <xref:System.Windows.UIElement.OnDragLeave%2A> suivante pour fournir la gestion de classe pour l'événement <xref:System.Windows.UIElement.DragLeave>.  
  
     [!code-csharp[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]  
  
     Cette substitution <xref:System.Windows.UIElement.OnDragLeave%2A> exécute les tâches suivantes :  
  
    -   Applique le <xref:System.Windows.Media.Brush> enregistré dans la variable `_previousFill` à <xref:System.Windows.Shapes.Shape.Fill%2A> de <xref:System.Windows.Shapes.Ellipse> qui fournit l'interface utilisateur du contrôle utilisateur Circle.  
  
5.  Appuyez sur F5 pour générer et exécuter l'application.  
  
6.  Sélectionnez le mot `green` dans <xref:System.Windows.Controls.TextBox>.  
  
7.  Faites glisser le texte au\-dessus d'un contrôle Circle sans le déposer.  Le contrôle Circle passe du bleu au vert.  
  
     ![Afficher un aperçu du résultat de l'opération de glisser&#45;déplacer](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop\_PreviewEffects")  
  
8.  Faites glisser le texte en dehors du contrôle Circle.  Le contrôle Circle repasse du vert au bleu.  
  
## Activation d'un panneau pour recevoir des données déplacées  
 De cette section, vous allez permettre aux panneaux qui hébergent les contrôles utilisateur Circle de jouer le rôle de cibles de déplacement pour les données Circle glissées.  Vous allez implémenter un code qui vous permet de déplacer un contrôle Circle d'un panneau vers un autre, ou de créer une copie d'un contrôle Circle en maintenant la touche CTRL enfoncée tout en faisant glisser\-déposer un contrôle Circle.  
  
### Pour permettre au panneau d'être une cible de déplacement  
  
1.  Ouvrez MainWindow.xaml.  
  
2.  Comme indiqué dans le code XAML suivant, dans chacun des contrôles <xref:System.Windows.Controls.StackPanel>, ajoutez des gestionnaires pour les événements <xref:System.Windows.UIElement.DragOver> et <xref:System.Windows.UIElement.Drop>.  Nommez le gestionnaire d'événements <xref:System.Windows.UIElement.DragOver>, `panel_DragOver`, le gestionnaire d'événements <xref:System.Windows.UIElement.Drop>, `panel_Drop`.  
  
     [!code-xml[DragDropWalkthrough#PanelsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]  
  
3.  Ouvrez MainWindows.xaml.cs ou MainWindow.xaml.vb.  
  
4.  Ajoutez le code suivant pour le gestionnaire d'événements <xref:System.Windows.UIElement.DragOver>.  
  
     [!code-csharp[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]  
  
     Ce gestionnaire d'événements <xref:System.Windows.UIElement.DragOver> effectue les tâches suivantes :  
  
    -   Vérifie que les données glissées contiennent les données « Objet » qui ont été empaquetées dans <xref:system.Windows.DataObject> par le contrôle utilisateur Circle et passées dans l'appel à <xref:System.Windows.DragDrop.DoDragDrop%2A>.  
  
    -   Si les données « Objet » sont présentes, vérifie si la touche CTRL est enfoncée.  
  
    -   Si la touche CTRL est enfoncée, définit la propriété <xref:System.Windows.DragEventArgs.Effects%2A> sur <xref:System.Windows.DragDropEffects>.  La propriété <xref:System.Windows.DragEventArgs.Effects%2A> a pour valeur <xref:System.Windows.DragDropEffects>.  
  
5.  Ajoutez le code suivant pour le gestionnaire d'événements <xref:System.Windows.UIElement.Drop>.  
  
     [!code-csharp[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]  
  
     Ce gestionnaire d'événements <xref:System.Windows.UIElement.Drop> effectue les tâches suivantes :  
  
    -   Vérifie si l'événement <xref:System.Windows.UIElement.Drop> a déjà été traité.  Par exemple, si un contrôle Circle est déposé sur un autre contrôle Circle qui gère l'événement <xref:System.Windows.UIElement.Drop>, le panneau qui contient le contrôle Circle ne doit pas également le gérer.  
  
    -   Si l'événement <xref:System.Windows.UIElement.Drop> n'est pas géré, vérifie si la touche CTRL est enfoncée.  
  
    -   Si la touche CTRL est enfoncée lorsque l'événement <xref:System.Windows.UIElement.Drop> se produit, effectue une copie du contrôle Circle et l'ajoute à la collection <xref:System.Windows.Controls.Panel.Children%2A> de <xref:System.Windows.Controls.StackPanel>.  
  
    -   Si la touche CTRL n'est pas enfoncée, déplace le contrôle Circle de la collection <xref:System.Windows.Controls.Panel.Children%2A> de son panneau parent vers la collection <xref:System.Windows.Controls.Panel.Children%2A> du panneau sur lequel il a été déposé.  
  
    -   Définit la propriété <xref:System.Windows.DragEventArgs.Effects%2A> pour indiquer à la méthode <xref:System.Windows.DragDrop.DoDragDrop%2A> si une opération de déplacement ou de copie a été effectuée.  
  
6.  Appuyez sur F5 pour générer et exécuter l'application.  
  
7.  Sélectionnez le mot `green` dans <xref:System.Windows.Controls.TextBox>.  
  
8.  Faites glisser le texte au\-dessus d'un contrôle Circle et déposez\-le.  
  
9. Faites glisser un contrôle Circle du panneau gauche vers panneau droit et déposez\-le.  Le contrôle Circle est supprimé de la collection <xref:System.Windows.Controls.Panel.Children%2A> du panneau gauche et ajouté à la collection Children du panneau droit.  
  
10. Faites glisser un contrôle Circle depuis le panneau où il se trouve vers l'autre panneau et déposez\-le tout en appuyant sur la touche CTRL.  Le contrôle Circle est copié et la copie est ajoutée à la collection <xref:System.Windows.Controls.Panel.Children%2A> du panneau de destination.  
  
     ![Glissement d'un cercle tout en appuyant sur la touche CTRL](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop\_PanelDrop")  
  
## Voir aussi  
 [Vue d'ensemble du glisser\-déplacer](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)