---
title: "Procédure pas à pas : activation de la fonction glisser-déplacer sur un contrôle utilisateur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 360b453b2a25b6822485f18cc81cb43e313949eb
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a>Procédure pas à pas : activation de la fonction glisser-déplacer sur un contrôle utilisateur
Cette procédure pas à pas montre comment créer un contrôle utilisateur personnalisé qui peut participer à un transfert de données par glisser-déplacer dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 Dans cette procédure pas à pas, vous allez créer un WPF personnalisé <xref:System.Windows.Controls.UserControl> qui représente une forme de cercle. Vous implémentez la fonctionnalité sur le contrôle pour activer le transfert de données par glisser-déplacer. Par exemple, si vous faites glisser un contrôle de cercle sur un autre, les données de couleur de remplissage sont copiées du cercle source vers la cible. Si vous faites glisser un contrôle Circle à un <xref:System.Windows.Controls.TextBox>, la représentation sous forme de chaîne de la couleur de remplissage est copiée vers le <xref:System.Windows.Controls.TextBox>. Vous créerez également une petite application qui contient deux contrôles de panneau de configuration et un <xref:System.Windows.Controls.TextBox> pour tester la fonctionnalité de glisser-déplacer. Vous écrivez du code qui permet aux panneaux de traiter les données de cercle déplacées, ce qui vous permet de déplacer ou copier des cercles de la collection d’enfants d’un panneau à l’autre.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Créer un contrôle utilisateur personnalisé.  
  
-   Permettre au contrôle utilisateur d’être une source de glissement.  
  
-   Permettre au contrôle utilisateur d’être une cible de déplacement.  
  
-   Permettre à un panneau de recevoir des données déplacées à partir du contrôle utilisateur.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Visual Studio 2010  
  
## <a name="creating-the-application-project"></a>Création du projet d’application  
 Dans cette section, vous allez créer l’infrastructure d’application, qui comprend une page principale avec deux panneaux et un <xref:System.Windows.Controls.TextBox>.  
  
### <a name="to-create-the-project"></a>Pour créer le projet  
  
1.  Créez un projet d’application WPF en Visual Basic ou Visual C# nommé `DragDropExample`. Pour plus d'informations, consultez [Guide pratique pour créer un projet d'application WPF](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
2.  Ouvrez MainWindow.xaml.  
  
3.  Ajoutez le balisage suivant entre les balises <xref:System.Windows.Controls.Grid> balises.  
  
     Ce balisage crée l’interface utilisateur pour l’application de test.  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]  
  
## <a name="adding-a-new-user-control-to-the-project"></a>Ajout d'un nouveau contrôle utilisateur au projet  
 Dans cette section, vous ajoutez un nouveau contrôle utilisateur au projet.  
  
### <a name="to-add-a-new-user-control"></a>Pour ajouter un nouveau contrôle utilisateur  
  
1.  Dans le menu Projet, sélectionnez **Ajouter un contrôle utilisateur**.  
  
2.  Dans la boîte de dialogue Ajouter un nouvel élément, remplacez le nom par `Circle.xaml`, puis cliquez sur **Ajouter**.  
  
     Circle.XAML et son code-behind sont ajoutés au projet.  
  
3.  Ouvrez Circle.xaml.  
  
     Ce fichier doit contenir les éléments d’interface utilisateur du contrôle utilisateur.  
  
4.  Ajoutez le balisage suivant à la racine <xref:System.Windows.Controls.Grid> pour créer un contrôle utilisateur simple qui présente un cercle bleu comme interface utilisateur.  
  
     [!code-xaml[DragDropWalkthrough#EllipseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]  
  
5.  Ouvrez Circle.xaml.cs ou Circle.xaml.vb.  
  
6.  En C#, ajoutez le code suivant après le constructeur par défaut pour créer un constructeur de copie. En Visual Basic, ajoutez le code suivant pour créer un constructeur par défaut et un constructeur de copie.  
  
     Pour que le contrôle utilisateur puisse être copié, vous ajoutez une méthode de constructeur de copie dans le fichier code-behind. Dans le contrôle utilisateur de cercle simplifié, vous copiez uniquement les valeurs de remplissage et de taille du contrôle utilisateur.  
  
     [!code-csharp[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]  
  
### <a name="to-add-the-user-control-to-the-main-window"></a>Pour ajouter le contrôle utilisateur à la fenêtre principale  
  
1.  Ouvrez MainWindow.xaml.  
  
2.  Ajoutez le code XAML suivant à l’ouverture <xref:System.Windows.Window> balise pour créer une référence d’espace de noms XML à l’application actuelle.  
  
    ```  
    xmlns:local="clr-namespace:DragDropExample"  
    ```  
  
3.  Dans la première <xref:System.Windows.Controls.StackPanel>, ajoutez le code XAML suivant pour créer deux instances du contrôle utilisateur cercle dans le premier panneau.  
  
     [!code-xaml[DragDropWalkthrough#CirclesXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]  
  
     Le code XAML complet pour le panneau ressemble à ce qui suit.  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]  
  
## <a name="implementing-drag-source-events-in-the-user-control"></a>Implémentation d’événements de source de glissement dans le contrôle utilisateur  
 Dans cette section, vous remplace le <xref:System.Windows.UIElement.OnMouseMove%2A> (méthode) et lancer l’opération de glisser-déplacer.  
  
 Si une opération de glissement n’est démarrée (un bouton de la souris est enfoncé et la souris est déplacée), vous créez un package les données à transférer dans un <xref:System.Windows.DataObject>. Dans cet exemple, le contrôle de cercle empaquette trois éléments de données : une représentation sous forme de chaîne de sa couleur de remplissage, une double représentation de sa hauteur et une copie de lui-même.  
  
### <a name="to-initiate-a-drag-and-drop-operation"></a>Pour lancer une opération de glisser-déplacer  
  
1.  Ouvrez Circle.xaml.cs ou Circle.xaml.vb.  
  
2.  Ajoutez le code suivant <xref:System.Windows.UIElement.OnMouseMove%2A> override pour fournir la gestion de classe pour le <xref:System.Windows.UIElement.MouseMove> événement.  
  
     [!code-csharp[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]  
  
     Cela <xref:System.Windows.UIElement.OnMouseMove%2A> remplacement effectue les tâches suivantes :  
  
    -   Vérifie si le bouton gauche de la souris est enfoncé quand la souris se déplace.  
  
    -   Regroupe les données Circle dans un <xref:System.Windows.DataObject>. Dans cet exemple, le contrôle de cercle empaquette trois éléments de données : une représentation sous forme de chaîne de sa couleur de remplissage, une double représentation de sa hauteur et une copie de lui-même.  
  
    -   Appelle la méthode statique <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> méthode pour lancer l’opération de glisser-déplacer. Vous passez les trois paramètres suivants pour le <xref:System.Windows.DragDrop.DoDragDrop%2A> méthode :  
  
        -   `dragSource` : Référence à ce contrôle.  
  
        -   `data`– Les <xref:System.Windows.DataObject> créé dans le code précédent.  
  
        -   `allowedEffects`– Les opérations de glisser-déplacer autorisées qui sont <xref:System.Windows.DragDropEffects.Copy> ou <xref:System.Windows.DragDropEffects.Move>.  
  
3.  Appuyez sur F5 pour générer et exécuter l'application.  
  
4.  Cliquez sur un des contrôles Circle et faites-le glisser sur les panneaux, cercle et le <xref:System.Windows.Controls.TextBox>. Lorsque vous faites glisser sur le <xref:System.Windows.Controls.TextBox>, le curseur se transforme pour indiquer un déplacement.  
  
5.  Tout en faisant glisser un cercle sur le <xref:System.Windows.Controls.TextBox>, appuyez sur la touche CTRL ENFONCÉE. Notez que le curseur change pour indiquer une copie.  
  
6.  Faites glisser et déposez un cercle sur le <xref:System.Windows.Controls.TextBox>. La représentation sous forme de chaîne de couleur de remplissage du cercle est ajoutée à la <xref:System.Windows.Controls.TextBox>.  
  
     ![Représentation sous forme de chaîne de la couleur de remplissage du cercle](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")  
  
 Par défaut, le curseur change pendant une opération de glisser-déplacer pour indiquer l’effet du déplacement des données. Vous pouvez personnaliser les commentaires donnés à l’utilisateur en gérant le <xref:System.Windows.UIElement.GiveFeedback> événement et en définissant un autre curseur.  
  
### <a name="to-give-feedback-to-the-user"></a>Pour transmettre des commentaires à l’utilisateur  
  
1.  Ouvrez Circle.xaml.cs ou Circle.xaml.vb.  
  
2.  Ajoutez le code suivant <xref:System.Windows.UIElement.OnGiveFeedback%2A> override pour fournir la gestion de classe pour le <xref:System.Windows.UIElement.GiveFeedback> événement.  
  
     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]  
  
     Cela <xref:System.Windows.UIElement.OnGiveFeedback%2A> remplacement effectue les tâches suivantes :  
  
    -   Vérifie la <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> valeurs qui sont définies dans la cible de dépôt <xref:System.Windows.UIElement.DragOver> Gestionnaire d’événements.  
  
    -   Définit un curseur personnalisé basé sur le <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> valeur. Le curseur a pour objectif de fournir des commentaires visuels à l’utilisateur sur l’effet du déplacement des données.  
  
3.  Appuyez sur F5 pour générer et exécuter l'application.  
  
4.  Faites glisser un de cercle contrôle sur les panneaux, cercle, et le <xref:System.Windows.Controls.TextBox>. Notez que les curseurs sont à présent les curseurs personnalisés que vous avez spécifié dans le <xref:System.Windows.UIElement.OnGiveFeedback%2A> remplacer.  
  
     ![Glisser-déplacer avec des curseurs personnalisés](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")  
  
5.  Sélectionnez le texte `green` à partir de la <xref:System.Windows.Controls.TextBox>.  
  
6.  Faites glisser le texte `green` sur un contrôle de cercle. Notez que les curseurs par défaut sont affichés pour indiquer les effets de l’opération de glisser-déplacer. Le curseur de commentaire est toujours défini par la source de glissement.  
  
## <a name="implementing-drop-target-events-in-the-user-control"></a>Implémentation d’événements de cible de déplacement dans le contrôle utilisateur  
 Dans cette section, vous indiquez que le contrôle utilisateur est une cible de déplacement, vous substituez les méthodes qui permettent au contrôle utilisateur d’être une cible de déplacement et vous traitez les données qui sont déplacées sur celui-ci.  
  
### <a name="to-enable-the-user-control-to-be-a-drop-target"></a>Pour permettre au contrôle utilisateur d’être une cible de déplacement  
  
1.  Ouvrez Circle.xaml.  
  
2.  Dans l’ouverture <xref:System.Windows.Controls.UserControl> , ajoutez le <xref:System.Windows.UIElement.AllowDrop%2A> propriété et affectez-lui la valeur `true`.  
  
     [!code-xaml[DragDropWalkthrough#UCTagXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]  
  
 Le <xref:System.Windows.UIElement.OnDrop%2A> méthode est appelée lorsque le <xref:System.Windows.UIElement.AllowDrop%2A> est définie sur `true` et données à partir de la source de glissement sont supprimées sur le contrôle utilisateur Circle. Dans cette méthode, vous traitez les données qui ont été déplacées et appliquez les données au cercle.  
  
### <a name="to-process-the-dropped-data"></a>Pour traiter les données déplacées  
  
1.  Ouvrez Circle.xaml.cs ou Circle.xaml.vb.  
  
2.  Ajoutez le code suivant <xref:System.Windows.UIElement.OnDrop%2A> override pour fournir la gestion de classe pour le <xref:System.Windows.UIElement.Drop> événement.  
  
     [!code-csharp[DragDropWalkthrough#OnDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]  
  
     Cela <xref:System.Windows.UIElement.OnDrop%2A> remplacement effectue les tâches suivantes :  
  
    -   Utilise le <xref:System.Windows.DataObject.GetDataPresent%2A> méthode permettant de vérifier si les données glissées contiennent un objet string.  
  
    -   Utilise le <xref:System.Windows.DataObject.GetData%2A> méthode pour extraire les données de chaîne si elle est présente.  
  
    -   Utilise un <xref:System.Windows.Media.BrushConverter> tente de convertir la chaîne en un <xref:System.Windows.Media.Brush>.  
  
    -   Si la conversion réussit, applique le pinceau pour le <xref:System.Windows.Shapes.Shape.Fill%2A> de la <xref:System.Windows.Shapes.Ellipse> qui fournit l’interface utilisateur du contrôle Circle.  
  
    -   Marque le <xref:System.Windows.UIElement.Drop> événement comme géré. Vous devez marquer l’événement de déplacement comme étant géré pour que les autres éléments qui reçoivent cet événement sachent que le contrôle utilisateur de cercle l’a géré.  
  
3.  Appuyez sur F5 pour générer et exécuter l'application.  
  
4.  Sélectionnez le texte `green` dans le <xref:System.Windows.Controls.TextBox>.  
  
5.  Faites glisser le texte vers un contrôle de cercle et déplacez-le. Le cercle passe du bleu au vert.  
  
     ![Convertir une chaîne en pinceau](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")  
  
6.  Tapez le texte `green` dans le <xref:System.Windows.Controls.TextBox>.  
  
7.  Sélectionnez le texte `gre` dans le <xref:System.Windows.Controls.TextBox>.  
  
8.  Faites le glisser vers un contrôle de cercle et déplacez-le. Notez que le curseur change pour indiquer que le déplacement est autorisé, mais la couleur du cercle ne change pas, car `gre` n’est pas une couleur valide.  
  
9. Faites glisser le contrôle de cercle vert et déplacez-le sur le contrôle de cercle bleu. Le cercle passe du bleu au vert. Notez que le curseur est affiché varie selon que le <xref:System.Windows.Controls.TextBox> ou le cercle vide est la source de glissement.  
  
 Définition de la <xref:System.Windows.UIElement.AllowDrop%2A> propriété `true` et traiter les données déplacées est tout ce qui est nécessaire pour activer un élément à une cible de dépôt. Toutefois, pour fournir une meilleure expérience utilisateur, vous devez également gérer les <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, et <xref:System.Windows.UIElement.DragOver> événements. Dans ces événements, vous pouvez effectuer des vérifications et fournir des commentaires supplémentaires à l’utilisateur avant de déplacer les données.  
  
 Quand les données sont glissées sur le contrôle utilisateur de cercle, le contrôle doit notifier la source de glissement si elle peut ou non traiter les données en cours de glissement. Si le contrôle ne sait pas comment traiter les données, il doit refuser le déplacement. Pour ce faire, vous allez gérer les <xref:System.Windows.UIElement.DragOver> événement et définissez le <xref:System.Windows.DragEventArgs.Effects%2A> propriété.  
  
### <a name="to-verify-that-the-data-drop-is-allowed"></a>Pour vérifier que le déplacement de données est autorisé  
  
1.  Ouvrez Circle.xaml.cs ou Circle.xaml.vb.  
  
2.  Ajoutez le code suivant <xref:System.Windows.UIElement.OnDragOver%2A> override pour fournir la gestion de classe pour le <xref:System.Windows.UIElement.DragOver> événement.  
  
     [!code-csharp[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]  
  
     Cela <xref:System.Windows.UIElement.OnDragOver%2A> remplacement effectue les tâches suivantes :  
  
    -   Affecte la valeur <xref:System.Windows.DragEventArgs.Effects%2A> à la propriété <xref:System.Windows.DragDropEffects.None>.  
  
    -   Exécute les mêmes vérifications sont effectuées dans le <xref:System.Windows.UIElement.OnDrop%2A> méthode pour déterminer si le contrôle utilisateur Circle peut traiter les données glissées.  
  
    -   Si le contrôle utilisateur peut traiter les données, définit les <xref:System.Windows.DragEventArgs.Effects%2A> propriété <xref:System.Windows.DragDropEffects.Copy> ou <xref:System.Windows.DragDropEffects.Move>.  
  
3.  Appuyez sur F5 pour générer et exécuter l'application.  
  
4.  Sélectionnez le texte `gre` dans le <xref:System.Windows.Controls.TextBox>.  
  
5.  Faites glisser le texte vers un contrôle de cercle. Notez que le curseur change à présent pour indiquer que le déplacement n’est pas autorisé, car `gre` n’est pas une couleur valide.  
  
 Vous pouvez améliorer l’expérience utilisateur en appliquant un aperçu de l’opération de déplacement. Pour le contrôle utilisateur Circle, remplace le <xref:System.Windows.UIElement.OnDragEnter%2A> et <xref:System.Windows.UIElement.OnDragLeave%2A> méthodes. Lorsqu’il sont déplacées les données sur le contrôle, l’arrière-plan actuel <xref:System.Windows.Shapes.Shape.Fill%2A> est enregistré dans une variable d’espace réservé. La chaîne est ensuite convertie en un pinceau et appliquée à la <xref:System.Windows.Shapes.Ellipse> qui fournit du cercle l’interface utilisateur. Si les données sont déplacées hors du cercle sans en cours de suppression d’origine <xref:System.Windows.Shapes.Shape.Fill%2A> valeur est de nouveau appliquée au cercle.  
  
### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a>Pour afficher un aperçu du résultat de l’opération de glisser-déplacer  
  
1.  Ouvrez Circle.xaml.cs ou Circle.xaml.vb.  
  
2.  Dans la classe Circle, déclarez un private <xref:System.Windows.Media.Brush> variable nommée `_previousFill` et initialisez-le à `null`.  
  
     [!code-csharp[DragDropWalkthrough#Brush](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]  
  
3.  Ajoutez le code suivant <xref:System.Windows.UIElement.OnDragEnter%2A> override pour fournir la gestion de classe pour le <xref:System.Windows.UIElement.DragEnter> événement.  
  
     [!code-csharp[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]  
  
     Cela <xref:System.Windows.UIElement.OnDragEnter%2A> remplacement effectue les tâches suivantes :  
  
    -   Enregistre le <xref:System.Windows.Shapes.Shape.Fill%2A> propriété de la <xref:System.Windows.Shapes.Ellipse> dans le `_previousFill` variable.  
  
    -   Exécute les mêmes vérifications sont effectuées dans le <xref:System.Windows.UIElement.OnDrop%2A> méthode pour déterminer si les données peuvent être converties en un <xref:System.Windows.Media.Brush>.  
  
    -   Si les données sont converties à valide <xref:System.Windows.Media.Brush>, s’applique à la <xref:System.Windows.Shapes.Shape.Fill%2A> de la <xref:System.Windows.Shapes.Ellipse>.  
  
4.  Ajoutez le code suivant <xref:System.Windows.UIElement.OnDragLeave%2A> override pour fournir la gestion de classe pour le <xref:System.Windows.UIElement.DragLeave> événement.  
  
     [!code-csharp[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]  
  
     Cela <xref:System.Windows.UIElement.OnDragLeave%2A> remplacement effectue les tâches suivantes :  
  
    -   S’applique le <xref:System.Windows.Media.Brush> enregistrées dans le `_previousFill` variable à la <xref:System.Windows.Shapes.Shape.Fill%2A> de la <xref:System.Windows.Shapes.Ellipse> qui fournit l’interface utilisateur du contrôle utilisateur Circle.  
  
5.  Appuyez sur F5 pour générer et exécuter l'application.  
  
6.  Sélectionnez le texte `green` dans le <xref:System.Windows.Controls.TextBox>.  
  
7.  Faites glisser le texte sur un contrôle de cercle sans le déplacer. Le cercle passe du bleu au vert.  
  
     ![Prévisualiser les effets d’une opération de glisser-déplacer](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")  
  
8.  Faites glisser le texte en dehors du contrôle de cercle. Le cercle passe du vert au bleu.  
  
## <a name="enabling-a-panel-to-receive-dropped-data"></a>Permettre à un panneau de recevoir des données déplacées  
 Dans cette section, vous permettez aux panneaux qui hébergent les contrôles utilisateur de cercle d’agir comme des cibles de déplacement pour les données de cercle glissées. Vous implémentez le code qui vous permet de déplacer un cercle d’un panneau vers un autre ou d’effectuer une copie d’un contrôle de cercle en maintenant enfoncée la touche CTRL tout en effectuant un glisser-déplacer d’un cercle.  
  
### <a name="to-enable-the-panel-to-be-a-drop-target"></a>Pour permettre au panneau d’être une cible de déplacement  
  
1.  Ouvrez MainWindow.xaml.  
  
2.  Comme indiqué dans le code XAML suivant, dans chacun de la <xref:System.Windows.Controls.StackPanel> contrôles, ajouter des gestionnaires pour les <xref:System.Windows.UIElement.DragOver> et <xref:System.Windows.UIElement.Drop> événements. Nom de la <xref:System.Windows.UIElement.DragOver> Gestionnaire d’événements, `panel_DragOver`et nommez le <xref:System.Windows.UIElement.Drop> Gestionnaire d’événements, `panel_Drop`.  
  
     [!code-xaml[DragDropWalkthrough#PanelsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]  
  
3.  Ouvrez MainWindows.xaml.cs ou MainWindow.xaml.vb.  
  
4.  Ajoutez le code suivant pour le <xref:System.Windows.UIElement.DragOver> Gestionnaire d’événements.  
  
     [!code-csharp[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]  
  
     Cela <xref:System.Windows.UIElement.DragOver> Gestionnaire d’événements effectue les tâches suivantes :  
  
    -   Vérifie que les données glissées contiennent les données « Objet » qui a été créées dans le <xref:System.Windows.DataObject> par le contrôle utilisateur Circle et passées dans l’appel à <xref:System.Windows.DragDrop.DoDragDrop%2A>.  
  
    -   Si les données « Object » sont présentes, vérifie si la touche CTRL est enfoncée.  
  
    -   Si la touche CTRL, définit le <xref:System.Windows.DragEventArgs.Effects%2A> propriété <xref:System.Windows.DragDropEffects.Copy>. Sinon, la valeur du <xref:System.Windows.DragEventArgs.Effects%2A> propriété <xref:System.Windows.DragDropEffects.Move>.  
  
5.  Ajoutez le code suivant pour le <xref:System.Windows.UIElement.Drop> Gestionnaire d’événements.  
  
     [!code-csharp[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]  
  
     Cela <xref:System.Windows.UIElement.Drop> Gestionnaire d’événements effectue les tâches suivantes :  
  
    -   Vérifie si le <xref:System.Windows.UIElement.Drop> événement a déjà été traité. Par exemple, si un cercle est déplacé sur un autre contrôle Circle qui gère la <xref:System.Windows.UIElement.Drop> événement, vous ne souhaitez pas que le panneau de configuration qui contient le cercle également le gérer.  
  
    -   Si le <xref:System.Windows.UIElement.Drop> événement n'est pas géré, vérifie si la touche CTRL.  
  
    -   Si la touche CTRL est activée lorsque le <xref:System.Windows.UIElement.Drop> se produit, effectue une copie du cercle de contrôle et l’ajouter à la <xref:System.Windows.Controls.Panel.Children%2A> collection de la <xref:System.Windows.Controls.StackPanel>.  
  
    -   Si la touche CTRL n’est pas activée, déplace le cercle à partir de la <xref:System.Windows.Controls.Panel.Children%2A> collection de son panneau parent vers le <xref:System.Windows.Controls.Panel.Children%2A> collection du panneau qui il a été supprimé.  
  
    -   Définit le <xref:System.Windows.DragEventArgs.Effects%2A> propriété pour notifier le <xref:System.Windows.DragDrop.DoDragDrop%2A> (méthode) indique si une opération de déplacement ou de copie a été effectuée.  
  
6.  Appuyez sur F5 pour générer et exécuter l'application.  
  
7.  Sélectionnez le texte `green` à partir de la <xref:System.Windows.Controls.TextBox>.  
  
8.  Faites glisser le texte sur un contrôle de cercle et déplacez-le.  
  
9. Faites glisser un contrôle de cercle du panneau gauche vers le panneau droit et déplacez-le. Le cercle est supprimé de la <xref:System.Windows.Controls.Panel.Children%2A> collection du panneau gauche et ajouté à la collection Children du panneau droit.  
  
10. Faites glisser un contrôle de cercle du panneau dans lequel il se trouve vers l’autre panneau et déplacez-le en maintenant la touche CTRL enfoncée. Le cercle est copié et la copie est ajoutée à la <xref:System.Windows.Controls.Panel.Children%2A> collection du Panneau de réception.  
  
     ![Glissement d'un cercle en maintenant la touche CTRL enfoncée](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d'ensemble du glisser-déplacer](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
