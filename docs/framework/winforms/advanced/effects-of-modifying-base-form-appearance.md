---
title: "Cons&#233;quences de la modification de l&#39;aspect d&#39;un formulaire de base | Microsoft Docs"
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
  - "formulaires de base"
  - "héritage, formulaires"
  - "formulaires hérités, modifications d'un formulaire de base"
  - "formulaires parents"
  - "Windows Forms, apparence du formulaire de base"
ms.assetid: 1c3f2b29-a05c-4c6f-aa1a-4e66b94f343a
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Cons&#233;quences de la modification de l&#39;aspect d&#39;un formulaire de base
Durant le développement d'une application, vous devez parfois modifier l'aspect du formulaire de base dont sont hérités les autres formulaires du projet \(ou d'autres projets\).  
  
 Au moment du design, les modifications de l'aspect du formulaire de base \(qu'elles touchent à la définition des propriétés ou à l'ajout et au retrait de contrôles\) sont répercutées dans les formulaires hérités lorsque le projet contenant le formulaire de base est créé.  Il ne suffit pas de simplement enregistrer les modifications dans le formulaire de base.  Pour générer un projet, choisissez **Générer** dans le menu **Générer**.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Les modifications apportées au formulaire de base au moment de l'exécution n'ont aucune incidence sur les formulaires hérités déjà instanciés.  
  
## Voir aussi  
 [de base](../Topic/base%20\(C%23%20Reference\).md)   
 [Comment : hériter des Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)   
 [Héritage visuel des Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)