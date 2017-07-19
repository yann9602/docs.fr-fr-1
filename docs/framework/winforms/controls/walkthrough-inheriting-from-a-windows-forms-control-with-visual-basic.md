---
title: "Proc&#233;dure pas &#224; pas&#160;: h&#233;ritage &#224; partir d&#39;un contr&#244;le Windows Forms &#224; l&#39;aide de Visual&#160;Basic | Microsoft Docs"
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
  - "contrôles personnalisés (Windows Forms), héritage"
  - "héritage, contrôle"
  - "héritage, contrôles personnalisés"
  - "héritage, procédures pas à pas"
  - "contrôles Windows Forms, héritage"
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Proc&#233;dure pas &#224; pas&#160;: h&#233;ritage &#224; partir d&#39;un contr&#244;le Windows Forms &#224; l&#39;aide de Visual&#160;Basic
Avec [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], vous pouvez créer des contrôles personnalisés puissants par le biais de l'*héritage*.  L'héritage vous permet de créer des contrôles qui conservent toutes les fonctionnalités inhérentes des contrôles Windows Forms standard, mais qui intègrent également des fonctionnalités personnalisées.  Dans cette procédure, vous allez créer un contrôle hérité simple, appelé `ValueButton`.  Ce bouton héritera des fonctionnalités du contrôle Windows Forms standard <xref:System.Windows.Forms.Button>, et exposera une propriété personnalisée appelée `ButtonValue`.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Création du projet  
 Lorsque vous créez un projet, vous spécifiez son nom pour définir l'espace de noms racine, le nom de l'assembly ainsi que celui du projet et vous avez la garantie que le composant par défaut sera placé dans l'espace de noms adéquat.  
  
#### Pour créer la bibliothèque de contrôles ValueButtonLib et le contrôle ValueButton  
  
1.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet** pour ouvrir la boîte de dialogue **Nouveau projet**.  
  
2.  Sélectionnez le modèle de projet **Bibliothèque de contrôles Windows Forms** à partir de la liste de projets [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], puis tapez `ValueButtonLib` dans la zone **Nom**.  
  
     Le nom de projet, `ValueButtonLib`, est également assigné à l'espace de noms racine par défaut.  L'espace de noms racine sert à qualifier le nom des composants de l'assembly.  Par exemple, si deux assemblys contiennent des composants nommés `ValueButton`, vous pouvez spécifier votre composant `ValueButton` à l'aide de `ValueButtonLib.ValueButton`.  Pour plus d'informations, consultez [Espaces de noms dans Visual Basic](../Topic/Namespaces%20in%20Visual%20Basic.md).  
  
3.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **UserControl1.vb**, puis cliquez sur **Renommer** dans le menu contextuel.  Remplacez le nom de fichier par `ValueButton.vb`.  Cliquez sur le bouton **Oui** à la question de savoir si vous souhaitez renommer toutes les références à l'élément de code "UserControl1".  
  
4.  Dans l'**Explorateur de solutions**, cliquez sur le bouton **Afficher tous les fichiers**.  
  
5.  Ouvrez le nœud **ValueButton.vb** pour afficher le fichier de code généré par le concepteur, **ValueButton.Designer.vb**.  Ouvrez ce fichier dans l'**éditeur de code**.  
  
6.  Localisez l'instruction `Class`, `Partial Public Class ValueButton`, puis modifiez le type dont hérite ce contrôle en remplaçant <xref:System.Windows.Forms.UserControl> par <xref:System.Windows.Forms.Button>.  Cela permet à votre contrôle hérité d'hériter toutes les fonctionnalités du contrôle <xref:System.Windows.Forms.Button>.  
  
7.  Localisez la méthode `InitializeComponent` et supprimez la ligne qui assigne la propriété <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>.  Cette propriété n'existe pas dans le contrôle <xref:System.Windows.Forms.Button>.  
  
8.  Dans le menu **Fichier**, choisissez **Enregistrer tout** pour enregistrer le projet.  
  
     Remarquez qu'il n'y a plus de concepteur visuel disponible.  Étant donné que le contrôle <xref:System.Windows.Forms.Button> définit sa propre apparence, vous ne pouvez pas la modifier dans le concepteur.  Sa représentation graphique sera exactement la même que celle de la classe dont il hérite \(à savoir, <xref:System.Windows.Forms.Button>\), sauf si elle est modifiée dans le code.  
  
> [!NOTE]
>  Vous pouvez encore ajouter des composants qui n'ont pas d'éléments d'interface utilisateur à l'aire de conception.  
  
## Ajout d'une propriété à un contrôle hérité  
 Entre autres usages, les contrôles Windows Forms hérités peuvent être employés pour créer des contrôles identiques en apparence aux contrôles Windows Forms standard, mais exposant des propriétés personnalisées.  Dans cette section, vous ajouterez à votre contrôle une propriété appelée `ButtonValue`.  
  
#### Pour ajouter la propriété Value  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **ValueButton.vb**, puis cliquez sur **Afficher le code** dans le menu contextuel.  
  
2.  Recherchez l'instruction `Public Class ValueButton`.  Immédiatement sous cette instruction, tapez le code suivant :  
  
     \[Visual Basic\]  
  
    ```  
    ' Creates the private variable that will store the value of your   
    ' property.  
    Private varValue as integer  
    ' Declares the property.  
    Property ButtonValue() as Integer  
    ' Sets the method for retrieving the value of your property.  
       Get  
          Return varValue  
       End Get  
    ' Sets the method for setting the value of your property.  
       Set(ByVal Value as Integer)  
          varValue = Value  
       End Set  
    End Property  
    ```  
  
     Ce code définit les méthodes par lesquelles la propriété `ButtonValue` est stockée et récupérée.  L'instruction `Get` définit comme valeur de retour la valeur stockée dans la variable privée `varValue`, et l'instruction `Set` définit la valeur de la variable privée à l'aide du mot clé `Value`.  
  
3.  Dans le menu **Fichier**, choisissez **Enregistrer tout** pour enregistrer le projet.  
  
## Test du contrôle  
 Les contrôles ne sont pas des projets autonomes ; ils doivent être hébergés dans un conteneur.  Pour tester votre contrôle, vous devez spécifier un projet de test dans lequel il s'exécutera.  Vous devez également rendre votre contrôle accessible au projet de test en le générant \(en le compilant\).  Dans cette section, vous allez générer un contrôle et le tester dans un Windows Form.  
  
#### Pour générer le contrôle  
  
1.  Dans le menu **Générer**, cliquez sur **Générer la solution**.  
  
     Cette opération devrait s'effectuer sans engendrer d'erreur de compilation ni d'avertissement.  
  
#### Pour créer un projet de test  
  
1.  Dans le menu **Fichier**, pointez sur **Ajouter**, puis cliquez sur **Nouveau projet** pour ouvrir la boîte de dialogue **Ajouter un nouveau projet**.  
  
2.  Sélectionnez le nœud de projets [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] puis cliquez sur **Application Windows Forms**.  
  
3.  Dans la zone **Nom**, tapez `Test`.  
  
4.  Dans l'**Explorateur de solutions**, cliquez sur le bouton **Afficher tous les fichiers**.  
  
5.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Références** de votre projet test, puis sélectionnez **Ajouter une référence** dans le menu contextuel afin d'afficher la boîte de dialogue **Ajouter une référence**.  
  
6.  Cliquez sur l'onglet **Projets**.  
  
7.  Cliquez sur l'onglet **Projets**.  Votre projet `ValueButtonLib` est répertorié sous **Nom du projet**.  Double\-cliquez sur le projet pour ajouter la référence au projet de test.  
  
8.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **Test** et sélectionnez **Générer**.  
  
#### Pour ajouter votre contrôle au formulaire  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **Form1.vb** et sélectionnez **Concepteur de vues** dans le menu contextuel.  
  
2.  Dans la **boîte à outils**, cliquez sur **Composants ValueButtonLib**.  Double\-cliquez sur **ValueButton**.  
  
     Un contrôle **ValueButton** apparaît dans le formulaire.  
  
3.  Cliquez avec le bouton droit sur **ValueButton** et sélectionnez **Propriétés** dans son menu contextuel.  
  
4.  Dans la fenêtre **Propriétés**, examinez les propriétés de ce contrôle.  Notez qu'elles sont identiques à celles qui sont exposées par un bouton standard, à cela près qu'il existe une propriété supplémentaire, `ButtonValue`.  
  
5.  Affectez à la propriété `ButtonValue` la valeur `5`.  
  
6.  Sous l'onglet **Tous les Windows Forms** de la **Boîte à outils**, double\-cliquez sur **Étiquette** pour ajouter un contrôle <xref:System.Windows.Forms.Label> au formulaire.  
  
7.  Amenez l'étiquette au centre du formulaire.  
  
8.  Double\-cliquez sur `ValueButton1`.  
  
     L'**éditeur de code** s'ouvre à l'événement `ValueButton1_Click`.  
  
9. Tapez la ligne de code suivante.  
  
     \[Visual Basic\]  
  
    ```  
    Label1.Text = CStr(ValueButton1.ButtonValue)  
    ```  
  
10. Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **Test**, puis sélectionnez **Définir comme projet de démarrage** dans le menu contextuel.  
  
11. Dans le menu **Déboguer**, cliquez sur **Démarrer le débogage**.  
  
     `Form1` apparaît.  
  
12. Cliquez sur `Valuebutton1`.  
  
     Le chiffre « 5 » est affiché dans `Label1` pour indiquer que la propriété `ButtonValue` de votre contrôle hérité a été passée à `Label1` via la méthode `ValueButton1_Click`.  Votre contrôle `ValueButton` hérite ainsi de toutes les fonctionnalités du bouton Windows Forms standard, mais expose une propriété personnalisée supplémentaire.  
  
## Voir aussi  
 [Procédure pas à pas : création d'un contrôle composite à l'aide de Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)   
 [Comment : afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)   
 [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)   
 [NOT IN BUILD: Inheritance in Visual Basic](http://msdn.microsoft.com/fr-fr/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [Component Authoring Walkthroughs](../Topic/Component%20Authoring%20Walkthroughs.md)