---
title: "Proc&#233;dure pas &#224; pas&#160;: assignation du contenu WPF sur les Windows Forms au moment du design | Microsoft Docs"
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
  - "ElementHost (contrôle), assigner un contenu WPF au moment du design"
  - "interopérabilité (WPF)"
  - "Windows Forms, assignations de contenu"
  - "contenu WPF (Windows Forms), assigner au moment du design"
  - "WPF (contrôle utilisateur), héberger dans les Windows Forms"
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Proc&#233;dure pas &#224; pas&#160;: assignation du contenu WPF sur les Windows Forms au moment du design
Cette procédure pas à pas montre comment sélectionner les types de contrôle WPF \(Windows Presentation Foundation\) que vous souhaitez afficher sur votre formulaire.  Vous pouvez sélectionner tout type de contrôle WPF inclus dans votre projet.  
  
 Lors de cette procédure pas à pas, vous allez exécuter les tâches suivantes :  
  
-   créer le projet ;  
  
-   créer les types de contrôles WPF ;  
  
-   sélectionner les contrôles WPF.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## Création du projet  
 La première étape consiste à créer le projet Windows Forms.  
  
> [!NOTE]
>  Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C\# sont pris en charge.  
  
#### Pour créer le projet  
  
-   Créez un projet d'application Windows Forms dans Visual Basic ou Visual C\# nommé `SelectingWpfContent`.  
  
## Création des types de contrôles WPF  
 Après avoir ajouté des types de contrôles WPF au projet, vous pouvez les héberger dans différents contrôles <xref:System.Windows.Forms.Integration.ElementHost>.  
  
#### Pour créer des types de contrôles WPF  
  
1.  Ajoutez un nouveau projet <xref:System.Windows.Controls.UserControl> WPF à la solution.  Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`.  Pour plus d'informations, consultez [Procédure pas à pas : création de contenu WPF sur les Windows Forms au moment du design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  En mode Design, assurez\-vous que `UserControl1` est sélectionné.  Pour plus d'informations, consultez [Comment : sélectionner et déplacer des éléments sur l'aire de conception](http://msdn.microsoft.com/fr-fr/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  Dans la fenêtre **Propriétés**, affectez la valeur `200` aux propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>.  
  
4.  Ajoutez un contrôle <xref:System.Windows.Controls.TextBox?displayProperty=fullName> au <xref:System.Windows.Controls.UserControl> et affectez la valeur Contenu hébergé à la propriété <xref:System.Windows.Controls.TextBox.Text%2A>.  
  
5.  Ajoutez un deuxième <xref:System.Windows.Controls.UserControl> WPF au projet.  Utilisez le nom par défaut pour le type de contrôle, `UserControl2.xaml`.  
  
6.  Dans la fenêtre **Propriétés**, affectez la valeur `200` aux propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>.  
  
7.  Ajoutez un contrôle <xref:System.Windows.Controls.TextBox?displayProperty=fullName> au <xref:System.Windows.Controls.UserControl> et affectez la valeur Contenu hébergé 2 à la propriété <xref:System.Windows.Controls.TextBox.Text%2A>.  
  
 **Remarque** En général, vous devez héberger du contenu WPF plus sophistiqué.  Le contrôle <xref:System.Windows.Controls.TextBox?displayProperty=fullName> est utilisé ici uniquement à titre d'illustration.  
  
1.  Générez le projet.  
  
## Sélection des contrôles WPF  
 Vous pouvez assigner du contenu WPF différent à un contrôle <xref:System.Windows.Forms.Integration.ElementHost> qui héberge déjà du contenu.  
  
#### Pour sélectionner des contrôles WPF  
  
1.  Ouvrez `Form1` dans le Concepteur Windows Forms.  
  
2.  Dans la **Boîte à outils**, double\-cliquez sur `UserControl1` pour créer une instance de `UserControl1` sur le formulaire.  
  
     Une instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.  
  
3.  Dans le panneau de Smart Tags pour `elementHost1`, ouvrez la liste déroulante **Sélectionner le contenu hébergé**.  
  
4.  Sélectionnez **UserControl2** dans la zone de liste déroulante.  
  
     Le contrôle `elementHost1` héberge maintenant une instance du type `UserControl2`.  
  
5.  Dans la fenêtre **Propriétés**, vérifiez que la propriété <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> a la valeur **UserControl2**.  
  
6.  Dans la **Boîte à outils**, dans le groupe **Interopérabilité WPF**, faites glisser un contrôle <xref:System.Windows.Forms.Integration.ElementHost> sur le formulaire.  
  
     Le nom par défaut du nouveau contrôle est `elementHost2`.  
  
7.  Dans le panneau de Smart Tags pour `elementHost2`, ouvrez la liste déroulante **Sélectionner le contenu hébergé**.  
  
8.  Sélectionnez **UserControl1** dans la liste déroulante.  
  
9. Le contrôle `elementHost2` héberge maintenant une instance du type `UserControl1`.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Migration et interopérabilité](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)   
 [Utilisation de contrôles WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)   
 [Concepteur WPF](http://msdn.microsoft.com/fr-fr/c6c65214-8411-4e16-b254-163ed4099c26)