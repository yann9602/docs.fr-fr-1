---
title: "Comment&#160;: extraire l&#39;ic&#244;ne associ&#233;e &#224; un fichier dans les Windows Forms | Microsoft Docs"
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
  - "afficher le nom d'un fichier et son icône de type de fichier dans un contrôle ListView (Windows Forms)"
  - "extraire les icônes associées à un type de fichier (Windows Forms)"
  - "icônes d'extension de nom de fichier (Windows Forms), afficher dans un ListView"
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: extraire l&#39;ic&#244;ne associ&#233;e &#224; un fichier dans les Windows Forms
De nombreux fichiers ont des icônes incorporées qui fournissent une représentation visuelle du type de fichier associé.  Par exemple, les documents Microsoft Word contiennent une icône qui les identifie comme documents Word.  Lorsque vous affichez des fichiers dans un contrôle List ou Table, vous pouvez afficher l'icône qui représente le type de fichier à côté de chaque nom de fichier.  Vous pouvez effectuer facilement cette opération en utilisant la méthode <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A>.  
  
## Exemple  
 L'exemple de code suivant montre comment extraire l'icône associée à un fichier et afficher le nom de fichier et son icône associée dans un contrôle <xref:System.Windows.Forms.ListView>.  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## Compilation du code  
 Pour compiler l'exemple :  
  
-   Collez le code précédent dans un Windows Form et appelez la méthode `ExtractAssociatedIconExample` du constructeur du formulaire ou la méthode <xref:System.Windows.Forms.Form.Load> de gestion d'événements.  
  
     Vous devez vous assurer que votre formulaire importe l'espace de noms <xref:System.IO>.  
  
## Voir aussi  
 [Images, bitmaps et métafichiers](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [ListView, contrôle](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)