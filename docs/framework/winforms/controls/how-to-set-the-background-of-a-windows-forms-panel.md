---
title: "Comment&#160;: d&#233;finir l&#39;arri&#232;re-plan d&#39;un panneau Windows Forms | Microsoft Docs"
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
  - "couleurs d'arrière-plan, contrôles Panel Windows Forms"
  - "images d'arrière-plan, contrôles Panel Windows Forms"
  - "couleurs, contrôles Panel Windows Forms"
  - "Panel (contrôle Windows Forms), arrière-plan"
ms.assetid: 096cbd8d-45cc-47b8-b1ef-a27f60ea8be0
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: d&#233;finir l&#39;arri&#232;re-plan d&#39;un panneau Windows Forms
Un contrôle <xref:System.Windows.Forms.Panel> Windows Forms peut afficher une couleur et une image d'arrière\-plan.  La propriété <xref:System.Windows.Forms.Control.BackColor%2A> définit la couleur d'arrière\-plan des contrôles contenus, par exemple les étiquettes et cases d'option.  Si la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A> n'est pas définie, la couleur <xref:System.Windows.Forms.Control.BackColor%2A> sélectionnée remplit tout le contrôle Panel.  Si la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A> est définie, l'image est affichée derrière les contrôles contenus.  
  
### Pour définir un arrière\-plan par programme  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.Control.BackColor%2A> du contrôle Panel une valeur de type <xref:System.Drawing.Color?displayProperty=fullName>.  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2.  Définissez la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A> du contrôle Panel à l'aide de la méthode <xref:System.Drawing.Image.FromFile%2A> de la classe <xref:System.Drawing.Image?displayProperty=fullName>.  
  
    ```vb  
    ' You should replace the bolded image   
    ' in the sample below with an image of your own choosing.  
    Panel1.BackgroundImage = Image.FromFile _  
        (System.Environment.GetFolderPath _  
        (System.Environment.SpecialFolder.Personal) _  
        & "\Image.gif")  
  
    ```  
  
    ```csharp  
    // You should replace the bolded image   
    // in the sample below with an image of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    panel1.BackgroundImage = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
  
    ```  
  
    ```cpp  
    // You should replace the bolded image   
    // in the sample below with an image of your own choosing.  
    panel1->BackgroundImage = Image::FromFile(String::Concat(  
       System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\Image.gif"));  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.Control.BackColor%2A>   
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>   
 [Panel, contrôle](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)   
 [Vue d'ensemble du contrôle Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)