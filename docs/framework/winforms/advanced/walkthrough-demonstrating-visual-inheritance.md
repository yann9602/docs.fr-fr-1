---
title: "Proc&#233;dure pas &#224; pas&#160;: d&#233;monstration de l&#39;h&#233;ritage visuel | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "héritage de formulaire, procédures pas à pas"
  - "héritage, procédures pas à pas"
  - "héritage visuel"
  - "procédures pas à pas (Windows Forms), héritage visuel"
  - "Windows Forms, héritage"
ms.assetid: 01966086-3142-450e-8210-3fd4cb33f591
caps.latest.revision: 24
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# Proc&#233;dure pas &#224; pas&#160;: d&#233;monstration de l&#39;h&#233;ritage visuel
L'héritage visuel vous permet de visualiser les contrôles sur le formulaire de base et d'ajouter de nouveaux contrôles.  Dans cette procédure pas à pas, vous allez créer un formulaire de base et le compiler dans une bibliothèque de classes.  Vous importerez cette bibliothèque de classes dans un autre projet et créerez un formulaire qui hérite du formulaire de base.  Pendant cette procédure pas à pas, vous allez apprendre à :  
  
-   créer un projet de bibliothèque de classes contenant un formulaire de base ;  
  
-   ajouter un bouton avec des propriétés modifiables par les classes dérivées du formulaire de base ;  
  
-   ajouter un bouton qui ne peut pas être modifié par les héritiers du formulaire de base ;  
  
-   créer un projet contenant un formulaire qui hérite de `BaseForm`.  
  
 Pour finir, cette procédure pas à pas vous montrera la différence entre les contrôles privés et protégés dans un formulaire hérité.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
> [!CAUTION]
>  Les contrôles ne prennent pas tous en charge l'héritage visuel à partir d'un formulaire de base.  Les contrôles suivants ne prennent pas en charge le scénario décrit dans cette procédure pas à pas :  
>   
>  <xref:System.Windows.Forms.WebBrowser>  
>   
>  <xref:System.Windows.Forms.ToolStrip>  
>   
>  <xref:System.Windows.Forms.ToolStripPanel>  
>   
>  <xref:System.Windows.Forms.TableLayoutPanel>  
>   
>  <xref:System.Windows.Forms.FlowLayoutPanel>  
>   
>  <xref:System.Windows.Forms.DataGridView>  
>   
>  Ces contrôles dans le formulaire hérité sont toujours en lecture seule, quels que soient les modificateurs que vous utilisez \(`private`, `protected` ou `public`\).  
  
## Étapes du scénario  
 La première étape consiste à créer le formulaire de base.  
  
#### Pour créer un projet de bibliothèque de classes contenant un formulaire de base  
  
1.  Dans le menu **Fichier**, choisissez **Nouveau**, puis **Projet** pour ouvrir la boîte de dialogue **Nouveau projet**.  
  
2.  Créez une application Windows Forms nommée `BaseFormLibrary`.  
  
3.  Pour créer une bibliothèque de classes au lieu d'une application Windows Forms standard, dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de projet **BaseFormLibrary**, puis sélectionnez **Propriétés**.  
  
4.  Dans les propriétés du projet, modifiez le **Type de sortie** en remplaçant **Application Windows** par **Bibliothèque de classes**.  
  
5.  Dans le menu **Fichier**, choisissez **Enregistrer tout** pour enregistrer les fichiers du projet à l'emplacement par défaut.  
  
 Les deux procédures suivantes ajoutent des boutons au formulaire de base.  Pour illustrer l'héritage visuel, donnez aux boutons différents niveaux d'accès en définissant leurs propriétés `Modifiers`.  
  
#### Pour ajouter un bouton modifiable par les héritiers du formulaire de base  
  
1.  Ouvrez **Form1** dans le concepteur.  
  
2.  Sous l'onglet **Tous les Windows Forms** de la **Boîte à outils**, double\-cliquez sur **Bouton** pour ajouter un bouton au formulaire.  Utilisez la souris pour positionner et redimensionner le bouton.  
  
3.  Dans la fenêtre Propriétés, définissez les propriétés suivantes du bouton :  
  
    -   Affectez la valeur **Say Hello** à la propriété **Texte**.  
  
    -   Affectez la valeur **btnProtected** à la propriété **\(Nom\)**.  
  
    -   Affectez la valeur **Protected** à la propriété **Modificateurs**.  Cela permet aux formulaires qui héritent de **Form1** de modifier les propriétés de **btnProtected**.  
  
4.  Double\-cliquez sur le bouton **Say Hello** pour ajouter un gestionnaire d'événements à l'événement **Click**.  
  
5.  Ajoutez la ligne de code suivante au gestionnaire d'événements :  
  
    ```vb  
    MessageBox.Show("Hello, World!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Hello, World!");  
    ```  
  
#### Pour ajouter un bouton qui ne peut pas être modifié par les héritiers du formulaire de base  
  
1.  Passez en mode Design en cliquant sur l'onglet **Form1.vb \[Design\], Form1.cs \[Design\] ou Form1.jsl \[Design\]** au\-dessus de l'éditeur de code, ou en appuyant sur F7.  
  
2.  Ajoutez un deuxième bouton et définissez ses propriétés comme suit :  
  
    -   Affectez la valeur **Say Goodbye** à la propriété **Texte**.  
  
    -   Affectez la valeur **btnPrivate** à la propriété **\(Nom\)**.  
  
    -   Affectez la valeur **Private** à la propriété **Modificateurs**.  Cela empêche les formulaires qui héritent de **Form1** de modifier les propriétés de **btnPrivate**.  
  
3.  Double\-cliquez sur le bouton **Say Goodbye** pour ajouter un gestionnaire d'événements à l'événement **Click**.  Placez la ligne de code suivante dans la procédure d'événement :  
  
    ```vb  
    MessageBox.Show("Goodbye!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Goodbye!");  
    ```  
  
4.  Dans le menu **Générer**, choisissez **Générer une bibliothèque BaseForm** pour générer la bibliothèque de classes.  
  
     Une fois la bibliothèque générée, vous pouvez créer un projet qui hérite du formulaire que vous venez de créer.  
  
#### Pour créer un projet contenant un formulaire qui hérite du formulaire de base  
  
1.  Dans le menu **Fichier**, choisissez **Ajouter**, puis **Nouveau projet** pour ouvrir la boîte de dialogue **Ajouter un nouveau projet**.  
  
2.  Créez une application Windows Forms nommée `InheritanceTest`.  
  
#### Pour ajouter un formulaire hérité  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **InheritanceTest**, sélectionnez **Ajouter**, puis **Nouvel élément**.  
  
2.  Dans la  boîte de dialogue **Ajouter un nouvel élément**, sélectionnez la catégorie **Windows Forms** \(si vous avez une liste de catégories\), puis sélectionnez le modèle **Formulaire hérité**.  
  
3.  Conservez le nom par défaut \(`Form2`\) et cliquez sur **Ajouter**.  
  
4.  Dans la boîte de dialogue **Sélecteur d'héritage**, sélectionnez **Form1** à partir du projet **BaseFormLibrary** comme formulaire à partir duquel hériter, puis cliquez sur **OK**.  
  
     Cela crée un formulaire dans le projet **InheritanceTest** qui dérive du formulaire dans **BaseFormLibrary**.  
  
5.  Ouvrez le formulaire hérité \(**Form2**\) dans le concepteur en double\-cliquant dessus, s'il n'est pas déjà ouvert.  
  
     Dans le concepteur, les boutons hérités ont un symbole \(![Capture d'écran VisualBasicInheritanceSymbol](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.png "vbInheritanceGlyph")\) dans le coin supérieur pour indiquer qu'ils sont hérités.  
  
6.  Sélectionnez le bouton **Say Hello** et observez les poignées de redimensionnement.  Ce bouton étant protégé, les héritiers peuvent le déplacer, le redimensionner, changer sa légende et apporter d'autres modifications.  
  
7.  Sélectionnez le bouton privé **Say Goodbye** et notez qu'il n'a pas de poignée de redimensionnement.  En outre, dans la fenêtre **Propriétés**, les propriétés de ce bouton sont estompées pour indiquer qu'elles ne sont pas modifiables.  
  
8.  Si vous utilisez [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] :  
  
    1.  Dans **l'Explorateur de solutions**, cliquez avec le bouton droit sur **Form1** dans le projet **InheritanceTest**, puis choisissez **Supprimer**.  Dans la boîte de message qui s'affiche, cliquez sur **OK** pour confirmer la suppression.  
  
    2.  Ouvrez le fichier Program.cs et remplacez la ligne `Application.Run(new Form1());` par `Application.Run(new Form2());`.  
  
9. Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **InheritanceTest** et sélectionnez **Définir comme projet de démarrage**.  
  
10. Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **InheritanceTest** et sélectionnez **Propriétés**.  
  
11. Dans les pages de propriétés **InheritanceTest**, définissez l'**Objet de démarrage** pour qu'il s'agisse du formulaire hérité \(**Form2**\).  
  
12. Appuyez sur F5 pour exécuter l'application et observez le comportement du formulaire hérité.  
  
## Étapes suivantes  
 L'héritage pour les contrôles utilisateur fonctionne de la même façon.  Ouvrez un nouveau projet de bibliothèque de classes et ajoutez un contrôle utilisateur.  Placez les contrôles constituants dessus et compilez le projet.  Ouvrez un autre projet de bibliothèque de classes et ajoutez une référence à la bibliothèque de classes compilée.  Essayez également d'ajouter un contrôle hérité \(via la boîte de dialogue **Ajouter de nouveaux éléments**\) au projet et d'utiliser le **Sélecteur d'héritage**.  Ajoutez un contrôle utilisateur et modifiez l'instruction `Inherits` \(`:` en [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]\).  Pour plus d'informations, consultez [Comment : hériter des Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md).  
  
## Voir aussi  
 [Comment : hériter des Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)   
 [Héritage visuel des Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)   
 [Windows Forms](../../../../docs/framework/winforms/index.md)