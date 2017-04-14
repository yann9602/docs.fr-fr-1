---
title: "Comment&#160;: h&#233;riter des Windows Forms | Microsoft Docs"
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
  - "héritage, formulaires"
  - "formulaires hérités, créer au moment de l'exécution"
  - "Windows Forms, héritage"
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: h&#233;riter des Windows Forms
Créer des Windows Forms en héritant de formulaires de base est un moyen pratique de dupliquer vos efforts sans avoir à recréer entièrement un formulaire chaque fois que vous en avez besoin.  
  
 Pour plus d'informations sur l'héritage des formulaires au moment du design à l'aide de la boîte de dialogue **Sélecteur d'héritage** et sur la façon d'effectuer une distinction visuelle entre les niveaux de sécurité des contrôles hérités, consultez [Comment : hériter de formulaires à l'aide de la boîte de dialogue Sélecteur d'héritage](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).  
  
 **Remarque** Pour hériter d'un formulaire, le fichier ou l'espace de noms contenant ce formulaire doit avoir été intégré à un fichier exécutable ou une DLL.  Pour générer le projet, choisissez **Générer** dans le menu **Générer**.  De plus, une référence à l'espace de noms doit être ajoutée à la classe héritant du formulaire.  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour hériter d'un formulaire par programmation  
  
1.  Dans votre classe, ajoutez une référence à l'espace de noms contenant le formulaire dont vous voulez hériter.  
  
2.  Dans la définition de classe, ajoutez une référence au formulaire à partir duquel hériter.  Cette référence doit inclure l'espace de noms qui contient le formulaire, suivi d'un point, puis du nom du formulaire de base proprement dit.  
  
    ```vb  
    Public Class Form2  
        Inherits Namespace1.Form1  
  
    ```  
  
    ```csharp  
    public class Form2 : Namespace1.Form1  
  
    ```  
  
 Lors de l'héritage de formulaires, n'oubliez pas que des problèmes peuvent survenir car les gestionnaires d'événements peuvent être appelés deux fois \(chaque événement étant géré par la classe de base et par la classe héritée\).  Pour plus d'informations sur la façon d'éviter ce problème, consultez [Dépannage des gestionnaires d'événements hérités dans Visual Basic](../Topic/Troubleshooting%20Inherited%20Event%20Handlers%20in%20Visual%20Basic.md).  
  
## Voir aussi  
 [Inherits Statement](../../../../ocs/visual-basic/language-reference/statements/inherits-statement.md)   
 [Imports Statement \(.NET Namespace and Type\)](../../../../ocs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [using](../Topic/using%20\(C%23%20Reference\).md)   
 [Conséquences de la modification de l'aspect d'un formulaire de base](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)   
 [Héritage visuel des Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)