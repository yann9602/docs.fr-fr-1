---
title: "Proc&#233;dure pas &#224; pas&#160;: d&#233;bogage des contr&#244;les Windows Forms personnalis&#233;s au moment du design | Microsoft Docs"
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
  - "contrôles (Windows Forms), débogage"
  - "contrôles personnalisés (Windows Forms), débogage"
  - "contrôles personnalisés (Windows Forms), procédures pas à pas"
  - "déboguer (Visual Studio), procédures pas à pas"
  - "déboguer (Visual Studio), Windows Forms"
  - "concepteurs"
  - "débogage en mode Design"
  - "éditeurs visuels"
  - "procédures pas à pas (Windows Forms), débogage"
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Proc&#233;dure pas &#224; pas&#160;: d&#233;bogage des contr&#244;les Windows Forms personnalis&#233;s au moment du design
Lorsque vous créez un contrôle personnalisé, vous constatez souvent qu'il est nécessaire de déboguer son comportement au moment du design.  C'est particulièrement vrai si vous créez un concepteur personnalisé pour votre contrôle personnalisé.  Pour plus d'informations, consultez [Procédure pas à pas : création d'un contrôle Windows Forms qui tire parti des fonctionnalités au moment du design de Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).  
  
 Vous pouvez déboguer vos contrôles personnalisés à l'aide de Visual Studio, comme vous le feriez avec des classes .NET Framework.  La différence est que vous déboguerez une instance séparée de Visual Studio qui exécute le code de votre contrôle personnalisé.  
  
 Cette procédure pas à pas illustre les tâches suivantes :  
  
-   Création d'un projet Windows Forms pour héberger votre contrôle personnalisé  
  
-   Création d'un projet de bibliothèque de contrôles  
  
-   Ajout d'une propriété à votre contrôle personnalisé  
  
-   Ajout de votre contrôle personnalisé au formulaire hôte  
  
-   Configuration du projet pour le débogage au moment du design  
  
-   Débogage de votre contrôle personnalisé au moment du design  
  
 Lorsque vous aurez terminé, vous aurez compris le fonctionnement des tâches nécessaires pour déboguer le comportement au moment du design d'un contrôle personnalisé.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Création du projet  
 La première étape consiste à créer le projet d'application.  Vous utiliserez ce projet pour générer l'application qui héberge le contrôle personnalisé.  
  
#### Pour créer le projet  
  
-   Créez un projet d'application Windows appelé « DebuggingExample ».  Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
## Création d'un projet de bibliothèque de contrôles  
 L'étape suivante consiste à créer le projet de bibliothèque de contrôles et à définir le contrôle personnalisé.  
  
#### Pour créer le projet de bibliothèque de contrôles  
  
1.  Ajoutez un projet de **bibliothèque de contrôles Windows** à la solution.  
  
2.  Ajoutez un nouvel élément **UserControl** au projet DebugControlLibrary.  Pour plus d'informations, consultez [NIB:How to: Add New Project Items](http://msdn.microsoft.com/fr-fr/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).  Donnez le nom de base « DebugControl » au nouveau fichier source.  
  
3.  À l'aide de l'**Explorateur de solutions**, supprimez le contrôle par défaut du projet en supprimant le fichier de code portant le nom de base « `UserControl1` ».  Pour plus d'informations, consultez [NIB:How to: Remove, Delete, and Exclude Items](http://msdn.microsoft.com/fr-fr/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).  
  
4.  Générez la solution.  
  
## Point de contrôle  
 À ce stade, vous serez en mesure de consulter votre contrôle personnalisé dans la **Boîte à outils**.  
  
#### Pour vérifier votre progression  
  
-   Recherchez le nouvel onglet appelé **Composants DebugControlLibrary** et cliquez pour le sélectionner.  Lorsqu'il s'ouvre, vous verrez votre contrôle répertorié comme **DebugControl** avec l'icône par défaut à côté de lui.  
  
## Ajout d'une propriété à votre contrôle personnalisé  
 Pour montrer que le code de votre contrôle personnalisé s'exécute au moment du design, vous ajouterez une propriété et définirez un point d'arrêt dans le code qui implémente la propriété.  
  
#### Pour ajouter une propriété à votre contrôle personnalisé  
  
1.  Ouvrez **DebugControl** dans l'**éditeur de code**.  Ajoutez le code suivant à la définition de classe :  
  
    ```vb  
    Private demoStringValue As String = Nothing  
    <BrowsableAttribute(true)>  
    Public Property DemoString() As String  
  
        Get  
            Return Me.demoStringValue  
        End Get  
  
        Set(ByVal value As String)  
            Me.demoStringValue = value  
        End Set  
  
    End Property  
    ```  
  
    ```csharp  
    private string demoStringValue = null;  
    [Browsable(true)]  
    public string DemoString  
    {  
        get  
        {  
            return this.demoStringValue;  
        }  
        set  
        {  
            demoStringValue = value;  
        }  
    }  
    ```  
  
2.  Générez la solution.  
  
## Ajout de votre contrôle personnalisé au formulaire hôte  
 Pour déboguer le comportement au moment du design de votre contrôle personnalisé, vous placerez une instance de la classe du contrôle personnalisé sur un formulaire hôte.  
  
#### Pour ajouter votre contrôle personnalisé au formulaire hôte  
  
1.  Dans le projet « DebuggingExample », ouvrez Form1 dans le **Concepteur Windows Forms**.  
  
2.  Dans la **boîte à outils**, ouvrez l'onglet **Composants DebugControlLibrary** et faites glisser une instance de **DebugControl** sur le formulaire.  
  
3.  Recherchez la propriété personnalisée `DemoString` dans la fenêtre **Propriétés**.  Notez que vous pouvez modifier sa valeur comme avec n'importe quelle autre propriété.  Notez également que lorsque la propriété `DemoString` est sélectionnée, la chaîne de description de la propriété apparaît en bas de la fenêtre **Propriétés**.  
  
## Configuration du projet pour le débogage au moment du design  
 Pour déboguer le comportement au moment du design de votre contrôle personnalisé, vous devez déboguer une instance séparée de Visual Studio qui exécute le code de votre contrôle personnalisé.  
  
#### Pour configurer le projet pour le débogage au moment du design  
  
1.  Cliquez avec le bouton droit sur le projet **DebugControlLibrary** dans l'**Explorateur de solutions**, puis sélectionnez **Propriétés**.  
  
2.  Dans la feuille de propriétés **DebugControlLibrary**, sélectionnez l'onglet **Déboguer**.  
  
     Dans la section **Action de démarrage**, sélectionnez **Démarrer le programme externe**.  Comme vous allez déboguer une instance séparée de Visual Studio, cliquez sur le bouton de sélection \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) pour rechercher l'IDE de Visual Studio.  Le nom du fichier exécutable est **devenv.exe** et, si vous avez effectué l'installation dans l'emplacement par défaut, son chemin d'accès est %programfiles%\\Microsoft Visual Studio 9.0\\Common7\\IDE\\devenv.exe.  
  
3.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
4.  Cliquez avec le bouton droit sur le projet  **DebugControlLibrary** et sélectionnez **Définir comme projet de démarrage** pour activer cette configuration de débogage.  
  
## Débogage de votre contrôle personnalisé au moment du design  
 Maintenant vous êtes prêt à déboguer votre contrôle personnalisé pendant il s'exécute en mode Design.  Lorsque vous démarrez la session de débogage, une nouvelle instance de Visual Studio est créée, et vous devez l'utiliser pour charger la solution « DebuggingExample ».  Lorsque vous ouvrez Form1 dans le **Concepteur Forms**, une instance de votre contrôle personnalisé est créée et commence à s'exécuter.  
  
#### Pour déboguer votre contrôle personnalisé au moment du design  
  
1.  Ouvrez le fichier source **DebugControl** dans l'**éditeur de code** et placez un point d'arrêt sur l'accesseur `Set` de la propriété `DemoString`.  
  
2.  Appuyez sur F5 pour démarrer la session de débogage.  Notez qu'une nouvelle instance de Visual Studio est créée.  Vous pouvez distinguer entre les instances de deux façons :  
  
    -   L'instance de débogage a le mot **En cours d'exécution** dans sa barre de titre  
  
    -   L'instance de débogage a le bouton **Démarrer** désactivé sur sa barre d'outils **Déboguer**  
  
     Votre point d'arrêt est défini dans l'instance de débogage.  
  
3.  Dans la nouvelle instance de Visual Studio, ouvrez la solution « DebuggingExample ».  Vous pouvez rechercher facilement la solution en sélectionnant **Projets récents** dans le menu **Fichier**.  Le fichier solution « DebuggingExample.sln » sera répertorié comme étant le dernier fichier utilisé.  
  
4.  Ouvrez Form1 dans le **Concepteur Forms** et sélectionnez le contrôle **DebugControl**.  
  
5.  Modifiez la valeur de la propriété `DemoString`.  Notez que lorsque vous validez la modification, l'instance de débogage de Visual Studio acquiert le focus et l'exécution s'arrête à votre point d'arrêt.  Vous pouvez lancer une exécution pas à pas à travers l'accesseur de propriété, comme vous le feriez pour n'importe quel autre code.  
  
6.  Lorsque vous avez terminé votre session de débogage, vous pouvez quitter en fermant l'instance hébergée de Visual Studio ou en cliquant sur le bouton **Arrêter le débogage** dans l'instance de débogage.  
  
## Étapes suivantes  
 Maintenant que vous pouvez déboguer vos contrôles personnalisés au moment du design, vous disposez de beaucoup de possibilités pour développer l'interaction de votre contrôle avec l'IDE de Visual Studio.  
  
-   Vous pouvez utiliser la propriété <xref:System.ComponentModel.Component.DesignMode%2A> de la classe <xref:System.ComponentModel.Component> pour écrire du code qui s'exécutera seulement au moment du design.  Pour plus d'informations, consultez <xref:System.ComponentModel.Component.DesignMode%2A>.  
  
-   Il existe plusieurs attributs que vous pouvez appliquer aux propriétés de votre contrôle pour manipuler l'interaction de votre contrôle personnalisé avec le concepteur.  Vous pouvez trouver ces attributs dans l'espace de noms <xref:System.ComponentModel?displayProperty=fullName>.  
  
-   Vous pouvez écrire un concepteur personnalisé pour votre contrôle personnalisé.  Vous aurez ainsi un contrôle complet sur l'expérience de design à l'aide de l'infrastructure du concepteur extensible exposée par Visual Studio.  Pour plus d'informations, consultez [Procédure pas à pas : création d'un contrôle Windows Forms qui tire parti des fonctionnalités au moment du design de Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).  
  
## Voir aussi  
 [Procédure pas à pas : création d'un contrôle Windows Forms qui tire parti des fonctionnalités au moment du design de Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)   
 [How to: Access Design\-Time Services](../Topic/How%20to:%20Access%20Design-Time%20Services.md)   
 [How to: Access Design\-Time Support in Windows Forms](../Topic/How%20to:%20Access%20Design-Time%20Support%20in%20Windows%20Forms.md)