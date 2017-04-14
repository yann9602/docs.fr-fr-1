---
title: "Comment&#160;: fournir une bitmap pour un contr&#244;le en vue de l&#39;afficher dans la bo&#238;te &#224; outils | Microsoft Docs"
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
  - "bitmaps (Windows Forms), contrôles personnalisés"
  - "contrôles personnalisés (Windows Forms), bitmaps (boîte à outils)"
  - "boîtes à outils (Windows Forms), ajouter des bitmaps pour les contrôles personnalisés"
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# Comment&#160;: fournir une bitmap pour un contr&#244;le en vue de l&#39;afficher dans la bo&#238;te &#224; outils
Si vous souhaitez qu'une icône spéciale pour votre contrôle apparaisse dans la **Boîte de dialogue**, vous pouvez spécifier une image particulière en utilisant le <xref:System.Drawing.ToolboxBitmapAttribute>.  Cette classe est un *attribut*, c'est\-à\-dire un type spécial de classe que vous pouvez attacher à d'autres classes.  Pour plus d'informations sur les attributs, consultez [NOT IN BUILD: Attributes Overview in Visual Basic](http://msdn.microsoft.com/fr-fr/0d0cff64-892d-4f57-83bd-bef388553d4f) pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] et [Attributs](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md) pour [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].  
  
 À l'aide de <xref:System.Drawing.ToolboxBitmapAttribute>, vous pouvez spécifier une chaîne qui indique le chemin d'accès et le nom de fichier d'une bitmap de 16 par 16 pixels.  Cette bitmap apparaît alors en regard de votre contrôle lorsqu'elle est ajoutée à la **Boîte à outils**.  Vous pouvez également spécifier une variable <xref:System.Type> afin que la bitmap associée à ce type soit chargée.  Si vous spécifiez à la fois un <xref:System.Type> et une chaîne, le contrôle recherche une ressource d'image avec le nom spécifié par le paramètre de chaîne dans l'assembly contenant le type spécifié par le paramètre  <xref:System.Type>.  
  
### Pour spécifier une bitmap pour votre contrôle en vue de l'afficher dans la boîte à outils  
  
1.  Ajoutez <xref:System.Drawing.ToolboxBitmapAttribute> à la déclaration de classe de votre contrôle avant le mot clé `Class` pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] et au\-dessus de la déclaration de classe pour [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].  
  
    ```vb  
    ' Specifies the bitmap associated with the Button type.  
    <ToolboxBitmap(GetType(Button))> Class MyControl1  
    ' Specifies a bitmap file.  
    End Class  
    <ToolboxBitmap("C:\Documents and Settings\Joe\MyPics\myImage.bmp")> _  
       Class MyControl2  
    End Class  
    ' Specifies a type that indicates the assembly to search, and the name   
    ' of an image resource to look for.  
    <ToolboxBitmap(GetType(MyControl), "MyControlBitmap")> Class MyControl  
    End Class  
    ```  
  
    ```csharp  
    // Specifies the bitmap associated with the Button type.  
    [ToolboxBitmap(typeof(Button))]  
    class MyControl1 : UserControl  
    {  
    }  
    // Specifies a bitmap file.  
    [ToolboxBitmap(@"C:\Documents and Settings\Joe\MyPics\myImage.bmp")]  
    class MyControl2 : UserControl  
    {  
    }  
    // Specifies a type that indicates the assembly to search, and the name   
    // of an image resource to look for.  
    [ToolboxBitmap(typeof(MyControl), "MyControlBitmap")]  
    class MyControl : UserControl  
    {  
    }  
    ```  
  
2.  Régénérez le projet.  
  
    > [!NOTE]
    >  La bitmap n'apparaît pas dans la Boîte à outils pour les composants et les contrôles générés automatiquement.  Pour afficher la bitmap, rechargez le contrôle à l'aide de la boîte de dialogue **Choisir des éléments de boîte à outils**.  Pour plus d'informations, consultez [Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
## Voir aussi  
 <xref:System.Drawing.ToolboxBitmapAttribute>   
 [Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)   
 [Développement de contrôles Windows Forms au moment du design](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)   
 [Attributes](../Topic/Attributes%20\(Visual%20Basic\)1.md)   
 [Attributs](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)