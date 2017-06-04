---
title: "Marge et marge int&#233;rieure dans les contr&#244;les Windows Forms | Microsoft Docs"
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
  - "disposition (Windows Forms), marges et marge intérieure"
  - "Margin (propriété Windows Forms)"
  - "Padding (propriété Windows Forms)"
  - "Windows Forms, disposition"
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Marge et marge int&#233;rieure dans les contr&#244;les Windows Forms
Le positionnement précis des contrôles sur votre formulaire constitue une haute priorité pour de nombreuses applications.  L'espace de noms <xref:System.Windows.Forms?displayProperty=fullName> propose pour cela de nombreuses fonctionnalités de disposition.  Deux des plus importantes sont les propriétés <xref:System.Windows.Forms.Control.Margin%2A> et <xref:System.Windows.Forms.Control.Padding%2A>.  
  
 La propriété <xref:System.Windows.Forms.Control.Margin%2A> définit l'espace autour du contrôle qui maintient les autres contrôles à une distance spécifiée des bordures du contrôle.  
  
 La propriété <xref:System.Windows.Forms.Control.Padding%2A> définit l'espace à l'intérieur d'un contrôle qui maintient le contenu du contrôle \(par exemple la valeur de sa propriété <xref:System.Windows.Forms.Control.Text%2A>\) à une distance spécifiée des bordures du contrôle.  
  
 L'illustration suivante montre les propriétés <xref:System.Windows.Forms.Control.Padding%2A> et <xref:System.Windows.Forms.Control.Margin%2A> d'un contrôle.  
  
 ![Remplissage et marge pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS\_WinFormPadMargin")  
  
 Cette fonctionnalité est prise en charge au moment du design dans Visual Studio.  Consultez également [Procédure pas à pas : disposition des contrôles Windows Forms avec les propriétés Padding, Margins et AutoSize](http://msdn.microsoft.com/library/3z3f9e8b%20\(v=vs.110\)).  
  
## Voir aussi  
 <xref:System.Windows.Forms.Control.AutoSize%2A>   
 <xref:System.Windows.Forms.Control.Margin%2A>   
 <xref:System.Windows.Forms.Control.Padding%2A>   
 <xref:System.Windows.Forms.Control.LayoutEngine%2A>   
 <xref:System.Windows.Forms.TableLayoutPanel>   
 <xref:System.Windows.Forms.FlowLayoutPanel>