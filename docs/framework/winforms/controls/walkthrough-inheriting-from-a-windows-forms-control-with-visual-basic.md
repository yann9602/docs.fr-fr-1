---
title: "Procédure pas à pas : héritage à partir d'un contrôle Windows Forms à l'aide de Visual Basic"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0625695933b776b8cdbe5488adc116723b930dd0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a>Procédure pas à pas : héritage à partir d'un contrôle Windows Forms à l'aide de Visual Basic
Avec [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], vous pouvez créer des contrôles personnalisés puissants grâce à *l’héritage*. L’héritage vous permet de créer des contrôles qui conservent toutes les fonctionnalités inhérentes des contrôles Windows Forms standard, tout en intégrant des fonctionnalités personnalisées. Dans cette procédure pas à pas, vous allez créer un contrôle hérité simple appelé `ValueButton`. Ce bouton hérite des fonctionnalités de Windows Forms standard <xref:System.Windows.Forms.Button> contrôler et expose une propriété personnalisée nommée `ButtonValue`.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Création du projet  
 Lorsque vous créez un nouveau projet, vous spécifiez son nom afin de définir l’espace de noms racine, le nom de l’assembly et le nom de projet, et de vous assurer que le composant par défaut sera placé dans l’espace de noms approprié.  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>Pour créer la bibliothèque de contrôles ValueButtonLib et le contrôle ValueButton  
  
1.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet** pour ouvrir la boîte de dialogue **Nouveau projet**.  
  
2.  Dans la liste des projets [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], sélectionnez le modèle de projet **Bibliothèque de contrôles Windows Forms**, puis saisissez `ValueButtonLib` dans le champ **Nom**.  
  
     Le nom du projet, `ValueButtonLib`, est également assigné à l’espace de noms racine par défaut. L’espace de noms racine est utilisé pour qualifier les noms des composants dans l’assembly. Par exemple, si deux assemblies contiennent des composants nommés `ValueButton`, vous pouvez spécifier votre composant `ValueButton` à l’aide de `ValueButtonLib.ValueButton`. Pour plus d’informations, consultez l’article [Espaces de noms dans Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).  
  
3.  Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **UserControl1.vb**, puis sélectionnez **Renommer** dans le menu contextuel. Remplacez le nom de fichier par `ValueButton.vb`. Cliquez sur le bouton **Oui** lorsque l’on vous demande si vous souhaitez renommer toutes les références à l’élément de code « UserControl1 ».  
  
4.  Dans l’**Explorateur de solutions**, cliquez sur le bouton **Afficher tous les fichiers**.  
  
5.  Ouvrez le nœud **ValueButton.vb** pour afficher le fichier de code généré par le concepteur, **ValueButton.Designer.vb**. Ouvrez ce fichier dans **l’éditeur de code**.  
  
6.  Recherchez le `Class` instruction, `Partial Public Class ValueButton`et modifier le type à partir duquel ce contrôle hérite <xref:System.Windows.Forms.UserControl> à <xref:System.Windows.Forms.Button>. Cela permet à votre contrôle d’hériter de toutes les fonctionnalités de la <xref:System.Windows.Forms.Button> contrôle.  
  
7.  Recherchez le `InitializeComponent` (méthode) et supprimer la ligne qui assigne la <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> propriété. Cette propriété n’existe pas dans le <xref:System.Windows.Forms.Button> contrôle.  
  
8.  Dans le menu **Fichier**, sélectionnez **Enregistrer tout** pour enregistrer le projet.  
  
     Notez que plus aucun concepteur visuel n’est disponible. Étant donné que le <xref:System.Windows.Forms.Button> contrôle effectue sa propre peinture, vous ne pouvez pas modifier son apparence dans le concepteur. Représentation visuelle sera exactement le même que celui de la classe, elle hérite (autrement dit, <xref:System.Windows.Forms.Button>), sauf si la modification dans le code.  
  
> [!NOTE]
>  Vous pouvez toujours ajouter sur l’aide de conception des composants n’ayant aucun élément d’interface utilisateur.  
  
## <a name="adding-a-property-to-your-inherited-control"></a>Ajout d’une propriété à votre contrôle hérité  
 Les contrôles Windows Forms hérités permettent notamment de créer des contrôles ayant la même apparence et le même comportement (aspect) que les contrôles Windows Forms standard, mais qui exposent des propriétés personnalisées. Dans cette section, vous allez ajouter une propriété appelée `ButtonValue` à votre contrôle.  
  
#### <a name="to-add-the-value-property"></a>Pour ajouter la propriété Valeur  
  
1.  Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **ValueButton.vb**, puis cliquez sur **Afficher le code** dans le menu contextuel.  
  
2.  Recherchez l’instruction `Public Class ValueButton`. Juste en dessous de cette instruction, saisissez le code suivant :  
  
    ```vb  
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
  
     Ce code définit les méthodes utilisées pour stocker et récupérer la propriété `ButtonValue`. L’instruction `Get` définit la valeur retournée à la valeur stockée dans la variable privée `varValue`et l’instruction `Set` définit la valeur de la variable privée à l’aide du mot clé `Value`.  
  
3.  Dans le menu **Fichier**, sélectionnez **Enregistrer tout** pour enregistrer le projet.  
  
## <a name="testing-your-control"></a>Test de votre contrôle  
 Les contrôles ne sont pas des projets autonomes ; ils doivent être hébergés dans un conteneur. Pour tester votre contrôle, vous devez fournir un projet de test dans lequel il sera exécuté. Vous devez également rendre votre contrôle accessible au projet de test en le générant (compilant). Dans cette section, vous allez générer votre contrôle et le tester dans un environnement Windows Form.  
  
#### <a name="to-build-your-control"></a>Pour générer votre contrôle  
  
1.  Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
     L’opération doit s’exécuter sans aucun avertissement ou erreur de compilation.  
  
#### <a name="to-create-a-test-project"></a>Pour créer un projet de test  
  
1.  Dans le menu **Fichier**, pointez vers**Ajouter**, puis cliquez sur **Nouveau projet** pour ouvrir la boîte de dialogue **Ajouter un nouveau projet**.  
  
2.  Sélectionnez le nœud de projets [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], puis cliquez sur **Application Windows Forms**.  
  
3.  Dans la zone **Nom**, tapez `Test`.  
  
4.  Dans l’**Explorateur de solutions**, cliquez sur le bouton **Afficher tous les fichiers**.  
  
5.  Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Références** de votre projet de test, puis sélectionnez **Ajouter une référence** dans le menu contextuel pour afficher la boîte de dialogue **Ajouter une référence**.  
  
6.  Cliquez sur l’onglet **Projets**.  
  
7.  Cliquez sur l’onglet intitulé **Projets**. Votre projet `ValueButtonLib` s’affiche sous **Nom du projet**. Double-cliquez sur le projet pour ajouter la référence au projet de test.  
  
8.  Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Test**, puis sélectionnez **Générer**.  
  
#### <a name="to-add-your-control-to-the-form"></a>Pour ajouter votre contrôle au formulaire  
  
1.  Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Form1.vb** et sélectionnez **Concepteur de vues** dans le menu contextuel.  
  
2.  Dans la **boîte à outils**, cliquez sur **Composants ValueButtonLib**. Double-cliquez sur **ValueButton**.  
  
     Un élément **ValueButton** apparaît sur le formulaire.  
  
3.  Cliquez avec le bouton droit sur l’élément **ValueButton** et sélectionnez **Propriétés** dans le menu contextuel.  
  
4.  Dans la fenêtre **Propriété**, examinez les propriétés de ce contrôle. Notez qu’elles sont identiques aux propriétés exposées par un bouton standard, à la différence près qu’il y a une propriété en plus, `ButtonValue`.  
  
5.  Affectez à la propriété `ButtonValue` la valeur `5`.  
  
6.  Sur le **tous les Windows Forms** onglet de la **boîte à outils**, double-cliquez sur **étiquette** pour ajouter un <xref:System.Windows.Forms.Label> à votre formulaire.  
  
7.  Déplacez l’étiquette au centre du formulaire.  
  
8.  Double-cliquez sur `ValueButton1`.  
  
     **L’éditeur de code** s’ouvre à l’événement `ValueButton1_Click`.  
  
9. Saisissez la ligne de code suivante.  
  
    ```vb  
    Label1.Text = CStr(ValueButton1.ButtonValue)  
    ```  
  
10. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Test** et sélectionnez **Définir comme projet de démarrage** dans le menu contextuel.  
  
11. Dans le menu **Déboguer**, sélectionnez **Démarrer le débogage**.  
  
     `Form1` s’affiche.  
  
12. Cliquez sur `Valuebutton1`.  
  
     Le chiffre « 5 » s’affiche dans `Label1`, ce qui prouve que la propriété `ButtonValue` de votre contrôle hérité a été définie sur `Label1` via la méthode `ValueButton1_Click`. Par conséquent, votre contrôle `ValueButton` hérite de toutes les fonctionnalités du bouton Windows Forms standard, mais expose en outre une propriété personnalisée supplémentaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : création d'un contrôle composite à l'aide de Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [Comment : afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Principes fondamentaux de l’héritage (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [Procédures pas à pas de la création de composants](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)
