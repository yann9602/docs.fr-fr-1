---
title: "Comment : naviguer parmi les données avec le contrôle BindingNavigator Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c5b49d84f98213e95c83c5476007297149adc16
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a>Comment : naviguer parmi les données avec le contrôle BindingNavigator Windows Forms
Le contrôle <xref:System.Windows.Forms.BindingNavigator> dans Windows Forms permet aux développeurs de fournir aux utilisateurs finaux une interface utilisateur de  navigation et de manipulation de données simple sur les formulaires qu'ils créent.  
  
 Le contrôle <xref:System.Windows.Forms.BindingNavigator> est un contrôle <xref:System.Windows.Forms.ToolStrip> avec des boutons préconfigurés pour la navigation vers quatre enregistrements (premier, dernier, suivant et précédent) dans un jeu de données, ainsi que des boutons pour ajouter et supprimer des enregistrements. L'ajout de boutons au contrôle <xref:System.Windows.Forms.BindingNavigator> est facile, car il s'agit d'un contrôle <xref:System.Windows.Forms.ToolStrip>.  Consultez également [Comment : ajouter des boutons Charger, Enregistrer et Annuler au contrôle BindingNavigator Windows Forms](http://msdn.microsoft.com/library/safa4957\(v=vs.110\)).  
  
 Pour chaque bouton sur le contrôle <xref:System.Windows.Forms.BindingNavigator>, il existe un membre correspondant du composant <xref:System.Windows.Forms.BindingSource> qui active par programmation la même fonctionnalité. Par exemple, le bouton <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> correspond à la méthode <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> du composant <xref:System.Windows.Forms.BindingSource>, le bouton <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> correspond à la méthode <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A>, et ainsi de suite. Ainsi, pour activer le contrôle <xref:System.Windows.Forms.BindingNavigator> pour parcourir des enregistrements de données, il suffit d'affecter à sa propriété <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> le composant <xref:System.Windows.Forms.BindingSource> approprié sur le formulaire.  
  
### <a name="to-set-up-the-bindingnavigator-control"></a>Pour configurer le contrôle BindingNavigator  
  
1.  Ajoutez un composant <xref:System.Windows.Forms.BindingSource> nommé `bindingSource1` et deux contrôles <xref:System.Windows.Forms.TextBox> nommés `textBox1` et `textBox2`.  
  
2.  Liez `bindingSource1` aux données et les contrôles de zone de texte à `bindingSource1`. Pour cela, collez le code suivant dans votre formulaire et appelez `LoadData` à partir de la méthode de gestion d'événements <xref:System.Windows.Forms.Form.Load> ou du constructeur du formulaire.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3.  Ajoutez un contrôle <xref:System.Windows.Forms.BindingNavigator> nommé `bindingNavigator1` à votre formulaire.  
  
4.  Définissez la propriété <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> pour `bindingNavigator1` et `bindingSource1`. Vous pouvez la définir avec le concepteur ou dans le code.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant est l'exemple complet pour les étapes répertoriées précédemment.  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System, System.Data, System.Drawing, System.Windows.Forms et System.Xml.  
  
 Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Génération à partir de la ligne de commande avec csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également la page [Comment : compiler et exécuter un exemple complet de code Windows Forms à l’aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.BindingNavigator>  
 [BindingNavigator, contrôle](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [Contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
