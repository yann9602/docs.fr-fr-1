---
title: "Vue d&#39;ensemble du contr&#244;le StatusStrip | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "StatusStrip"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "barres d'état, à propos des barres d'état"
  - "StatusStrip (contrôle Windows Forms), à propos du contrôle StatusStrip"
ms.assetid: c0d9bcbb-f8b8-46ef-bae2-4146b8c8ce99
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Vue d&#39;ensemble du contr&#244;le StatusStrip
Un contrôle <xref:System.Windows.Forms.StatusStrip> affiche des informations sur un objet affiché sur un <xref:System.Windows.Forms.Form>, les composants de l'objet ou des informations contextuelles relatives au fonctionnement de cet objet dans votre application.  En règle générale, un contrôle <xref:System.Windows.Forms.StatusStrip> est composé d'objets <xref:System.Windows.Forms.ToolStripStatusLabel>, chacun affichant du texte, une icône ou les deux.  <xref:System.Windows.Forms.StatusStrip> peut également contenir des contrôles <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton> et <xref:System.Windows.Forms.ToolStripProgressBar>.  
  
 Le <xref:System.Windows.Forms.StatusStrip> par défaut n'a pas de panneau.  Pour ajouter des panneaux à un <xref:System.Windows.Forms.StatusStrip>, utilisez la méthode <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=fullName>.  
  
 Visual Studio offre une prise en charge complète de la gestion des éléments et des commandes courantes de <xref:System.Windows.Forms.StatusStrip>.  
  
 Consultez également [Éditeur de collections d'éléments StatusStrip](http://msdn.microsoft.com/library/ms233631%20\(v=vs.110\)), [Tâches StatusStrip, boîte de dialogue](http://msdn.microsoft.com/library/ms233642%20\(v=vs.110\)).  
  
 Bien que <xref:System.Windows.Forms.StatusStrip> remplace et étende le contrôle <xref:System.Windows.Forms.StatusBar> des versions antérieures, <xref:System.Windows.Forms.StatusBar> est conservé à des fins de compatibilité descendante et pour une utilisation ultérieure si tel est votre choix.  
  
### Membres importants de StatusStrip  
  
|Nom|Description|  
|---------|-----------------|  
|<xref:System.Windows.Forms.StatusStrip.CanOverflow%2A>|Obtient ou définit une valeur indiquant si le <xref:System.Windows.Forms.StatusStrip> prend en charge les fonctionnalités de dépassement de capacité.|  
|<xref:System.Windows.Forms.StatusStrip.Stretch%2A>|Obtient ou définit une valeur indiquant si le <xref:System.Windows.Forms.StatusStrip> s'étire d'un bout à l'autre dans son <xref:System.Windows.Forms.ToolStripContainer>.|  
  
### Classes auxiliaires importantes de StatusStrip  
  
|Nom|Description|  
|---------|-----------------|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|Représente un panneau dans un contrôle <xref:System.Windows.Forms.StatusStrip>.|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|Affiche un <xref:System.Windows.Forms.ToolStripDropDown> associé à partir duquel l'utilisateur peut sélectionner un élément unique.|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|Représente un contrôle en deux parties constitué d'un bouton standard et d'un menu déroulant.|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|Affiche l'état d'achèvement d'un processus.|  
  
## Voir aussi  
 <xref:System.Windows.Forms.StatusStrip>   
 <xref:System.Windows.Forms.ToolStripStatusLabel>   
 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>