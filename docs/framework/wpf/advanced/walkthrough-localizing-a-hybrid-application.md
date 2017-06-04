---
title: "Proc&#233;dure pas &#224; pas&#160;: localisation d&#39;une application hybride | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "applications hybrides (interopérabilité WPF)"
  - "localisation (interopérabilité WPF)"
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Proc&#233;dure pas &#224; pas&#160;: localisation d&#39;une application hybride
Cette procédure pas à pas vous explique comment localiser des éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans une application hybride basée sur [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
 Cette procédure pas à pas illustre les tâches suivantes :  
  
-   Création du projet hôte [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
-   Ajout de contenu localisable.  
  
-   Activation de la localisation.  
  
-   Assignation des identificateurs de ressource.  
  
-   Utilisation de l'outil LocBaml pour produire un assembly satellite.  
  
 Pour obtenir l'intégralité du code correspondant aux tâches illustrées dans cette procédure pas à pas, consultez [Localisation d'une application hybride, exemple](http://go.microsoft.com/fwlink/?LinkID=160015).  
  
 Lorsque vous aurez terminé, vous disposerez d'une application hybride localisée.  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
## Création du projet hôte Windows Forms  
 La première étape consiste à créer le projet d'application [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et à ajouter un élément [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] avec du contenu que vous localiserez.  
  
#### Pour créer le projet hôte  
  
1.  Créez un projet Application WPF nommé `LocalizingWpfInWf`.  Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Ajoutez au projet un élément <xref:System.Windows.Controls.UserControl> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] appelé `SimpleControl`.  
  
3.  Utilisez le contrôle <xref:System.Windows.Forms.Integration.ElementHost> pour placer un élément `SimpleControl` sur le formulaire.  Pour plus d'informations, consultez [Procédure pas à pas : hébergement d'un contrôle composite 3\-D WPF dans les Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).  
  
## Ajout de contenu localisable  
 Vous allez ensuite ajouter un contrôle de type étiquette [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et affecter une chaîne localisable au contenu de l'élément [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
#### Pour ajouter du contenu localisable  
  
1.  Dans l'Explorateur de solutions, double\-cliquez sur **SimpleControl.xaml** afin de l'ouvrir dans le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
2.  Affectez le contenu du contrôle <xref:System.Windows.Controls.Button> à l'aide du code suivant.  
  
     [!code-xml[LocalizingWpfInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]  
  
3.  Dans l'Explorateur de solutions, double\-cliquez sur **Form1** afin de l'ouvrir dans le Concepteur Windows Forms.  
  
4.  Ouvrez la Boîte à outils et double\-cliquez sur **Label** pour ajouter un contrôle de type étiquette au formulaire.  Affectez `"Hello"` à la valeur de sa propriété <xref:System.Windows.Forms.Control.Text%2A>.  
  
5.  Appuyez sur F5 pour générer et exécuter l'application.  
  
     L'élément `SimpleControl` ainsi que le contrôle de type étiquette affichent le texte **"Hello"**.  
  
## Activation de la localisation  
 Le Concepteur Windows Forms fournit des paramètres pour activer la localisation dans un assembly satellite.  
  
#### Pour activer la localisation  
  
1.  Dans l'Explorateur de solutions, double\-cliquez sur **Form1.cs** afin de l'ouvrir dans le Concepteur Windows Forms.  
  
2.  Dans la fenêtre Propriétés, affectez la valeur `true` à la propriété **Localizable** du formulaire.  
  
3.  Dans la fenêtre Propriétés, affectez **Espagnol \(Espagne\)** à la valeur de la propriété **Language**.  
  
4.  Dans le Concepteur Windows Forms, sélectionnez le contrôle de type étiquette.  
  
5.  Dans la fenêtre Propriétés affectez `"Hola"` à la valeur de la propriété <xref:System.Windows.Forms.Control.Text%2A>.  
  
     Un nouveau fichier de ressources nommé Form1.es\-ES.resx est ajouté au projet.  
  
6.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **Form1.cs**, puis cliquez sur **Afficher le code** pour l'ouvrir dans l'éditeur de code.  
  
7.  Copiez le code suivant dans le constructeur `Form1`, précédant l'appel à `InitializeComponent`.  
  
     [!code-csharp[LocalizingWpfInWf#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]  
  
8.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **LocalizingWpfInWf**, puis cliquez sur **Décharger le projet**.  
  
     Le nom du projet est alors étiqueté **\(non disponible\)**.  
  
9. Cliquez avec le bouton droit sur **LocalizingWpfInWf**, puis cliquez sur **Modifier LocalizingWpfInWf.csproj**.  
  
     Le fichier projet s'ouvre dans l'éditeur de code.  
  
10. Copiez la ligne suivante dans le premier `PropertyGroup` du fichier projet.  
  
    ```  
    <UICulture>en-US</UICulture>   
    ```  
  
11. Enregistrez et fermez le fichier projet.  
  
12. Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **LocalizingWpfInWf**, puis cliquez sur **Recharger le projet**.  
  
## Assignation des identificateurs de ressource  
 Vous pouvez mapper votre contenu localisable à des assemblys de ressources en utilisant des identificateurs de ressource.  L'application MsBuild.exe assigne automatiquement des identificateurs de ressource lorsque vous spécifiez l'option `updateuid`.  
  
#### Pour assigner des identificateurs de ressource  
  
1.  Ouvrez l'invite de commandes [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] à partir du menu Démarrer.  
  
2.  Utilisez la commande suivante pour assigner des identificateurs de ressource à votre contenu localisable.  
  
    ```  
    msbuild /t:updateuid LocalizingWpfInWf.csproj  
    ```  
  
3.  Dans l'Explorateur de solutions, double\-cliquez sur **SimpleControl.xaml** afin de l'ouvrir dans l'éditeur de code.  Vous verrez que la commande `msbuild` a ajouté l'attribut `Uid` à tous les éléments.  Ceci facilite la localisation par l'assignation d'identificateurs de ressource.  
  
     [!code-xml[LocalizingWpfInWf#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]  
  
4.  Appuyez sur F6 pour générer la solution.  
  
## Utilisation de LocBaml pour produire un assembly satellite  
 Votre contenu localisé est stocké dans un *assembly satellite* consacré uniquement aux ressources.  Utilisez l'outil de ligne de commande LocBaml.exe pour produire un assembly localisé pour votre contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
#### Pour produire un assembly satellite  
  
1.  Copiez LocBaml.exe dans le dossier obj\\Debug de votre projet.  Pour plus d'informations, consultez [Localiser une application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).  
  
2.  Dans la fenêtre d'invite de commandes, utilisez la commande suivante pour extraire les chaînes de ressources dans un fichier temporaire.  
  
    ```  
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv  
    ```  
  
3.  Ouvrez le fichier temp.csv avec [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] ou un autre éditeur de texte.  Remplacez la chaîne `"Hello"` avec sa traduction en espagnol, `"Hola"`.  
  
4.  Enregistrez le fichier temp.csv.  
  
5.  Utilisez la commande suivante pour générer le fichier de ressources localisé.  
  
    ```  
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES  
    ```  
  
     Le fichier LocalizingWpfInWf.g.es\-ES.resources est créé dans le dossier obj\\Debug.  
  
6.  Utilisez la commande suivante pour générer l'assembly satellite localisé.  
  
    ```  
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources  
    ```  
  
     Le fichier LocalizingWpfInWf.resources.dll est créé dans le dossier obj\\Debug.  
  
7.  Copiez le fichier LocalizingWpfInWf.resources.dll file dans le dossier bin\\Debug\\es\-ES du projet.  Remplacez le fichier existant.  
  
8.  Exécutez LocalizingWpfInWf.exe, qui est situé dans le dossier bin\\Debug de votre projet.  Ne générez pas à nouveau l'application ou l'assembly satellite sera écrasé.  
  
     L'application affiche les chaînes localisées à la place des chaînes en anglais.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Localiser une application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)   
 [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/fr-fr/9a96220d-a19b-4de0-9f48-01e5d82679e5)   
 [Concepteur WPF](http://msdn.microsoft.com/fr-fr/c6c65214-8411-4e16-b254-163ed4099c26)