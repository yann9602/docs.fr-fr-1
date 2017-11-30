---
title: "Comment : lier des contrôles Windows Forms au composant BindingSource à l'aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18e89d0a236d3b370c521b73dfb640a09137a5dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a>Comment : lier des contrôles Windows Forms au composant BindingSource à l'aide du concepteur
Après avoir ajouté des contrôles à votre formulaire et de déterminer l’interface utilisateur pour votre application, vous pouvez lier les contrôles à une source de données, afin que, au moment de l’exécution, les utilisateurs peuvent modifier et enregistrer des données relatives à l’application.  
  
 Liaison d’un contrôle ou une série de contrôles dans les Windows Forms est plus facile à l’aide de la <xref:System.Windows.Forms.BindingSource> contrôle comme un pont entre les contrôles du formulaire et de la source de données.  
  
 Un ou plusieurs contrôles sur un formulaire peuvent être liés aux données ; dans la procédure suivante, un <xref:System.Windows.Forms.TextBox> contrôle est lié à une source de données.  
  
 Pour terminer la procédure, il est supposé que vous allez lier à une source de données dérivée d’une base de données. Pour plus d’informations sur la création de sources de données à partir d’autres magasins de données, consultez [ajouter de nouvelles sources de données](/visualstudio/data-tools/add-new-data-sources).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-bind-a-control-at-design-time"></a>Pour lier un contrôle au moment du design  
  
1.  Faites glisser un <xref:System.Windows.Forms.TextBox> contrôle au formulaire.  
  
2.  Dans le **propriétés** fenêtre :  
  
    1.  Développez le **(DataBindings)** nœud.  
  
    2.  Cliquez sur la flèche en regard du <xref:System.Windows.Forms.TextBox.Text%2A> propriété.  
  
         Le **DataSource** éditeur de type d’interface utilisateur s’ouvre.  
  
         Si une source de données a déjà été configurée pour le projet ou le formulaire, elle s’affiche.  
  
3.  Cliquez sur **Ajouter la source de données du projet** pour vous connecter aux données et créer une source de données.  
  
4.  Sur la page d’accueil de l’**Assistant Configuration de source de données**, cliquez sur **Suivant**.  
  
5.  Sur le **choisir un Type de Source de données** page, sélectionnez **base de données**.  
  
6.  Sur le **choisir votre connexion de données** , sélectionnez une connexion de données à partir de la liste des connexions disponibles. Si votre connexion de données souhaitée n’est pas disponible Sélectionnez **nouvelle connexion** pour créer une connexion de données.  
  
7.  Sélectionnez **Oui, enregistrer la connexion** pour enregistrer la chaîne de connexion dans le fichier de configuration d’application.  
  
8.  Sélectionnez les objets de base de données à mettre dans votre application. Dans ce cas, sélectionnez un champ dans une table que vous souhaitez que le <xref:System.Windows.Forms.TextBox> à afficher.  
  
9. Remplacez le nom du jeu de données par défaut, si vous le souhaitez.  
  
10. Cliquez sur **Terminer**.  
  
11. Dans le **propriétés** fenêtre, cliquez sur la flèche en regard du <xref:System.Windows.Forms.TextBox.Text%2A> propriété à nouveau. Dans le **DataSource** éditeur de type d’interface utilisateur, sélectionnez le nom du champ à lier le <xref:System.Windows.Forms.TextBox> à.  
  
     Le **DataSource** éditeur ferme et le jeu de données de type de l’interface utilisateur <xref:System.Windows.Forms.BindingSource> et l’adaptateur de table spécifique pour que la connexion de données sont ajoutés à votre formulaire.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [Ajouter de nouvelles sources de données](/visualstudio/data-tools/add-new-data-sources)  
 [Fenêtre Sources de données](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)
