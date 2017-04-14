---
title: "Vue d&#39;ensemble du contr&#244;le DomainUpDown (Windows Forms) | Microsoft Docs"
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
  - "DomainUpDown"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "DomainUpDown (contrôle Windows Forms), à propos du contrôle DomainUpDown"
  - "contrôle toupie, à propos de la toupie"
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Vue d&#39;ensemble du contr&#244;le DomainUpDown (Windows Forms)
Le contrôle <xref:System.Windows.Forms.DomainUpDown> Windows Forms se présente essentiellement comme une zone de texte à laquelle sont associés deux boutons permettant le déplacement vers le haut et vers le bas dans une liste.  Il affiche et définit une chaîne de texte provenant d'une liste d'options.  Pour sélectionner la chaîne, l'utilisateur peut se déplacer dans une liste en cliquant sur des boutons haut et bas, en appuyant sur les touches HAUT et BAS ou en tapant directement une chaîne correspondant à un élément de la liste.  Ce contrôle peut notamment être utilisé pour sélectionner des éléments dans une liste de noms triés par ordre alphabétique  
  
> [!NOTE]
>  \(pour trier la liste, affectez à la propriété <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> la valeur `true`\).  
  
 Ce contrôle a un fonctionnement très proche de celui des zones de liste simples ou déroulantes, mais il occupe un espace plus réduit.  
  
## Propriétés de clé  
 Les principales propriétés du contrôle sont <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> et <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.  La propriété <xref:System.Windows.Forms.DomainUpDown.Items%2A> contient la liste des objets dont les valeurs du texte sont affichées dans le contrôle.  Si la propriété <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> a la valeur `false`, le contrôle complète automatiquement le texte tapé par l'utilisateur et l'associe à une valeur de la liste.  Si la propriété <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> a la valeur `true`, vous revenez au premier élément de la liste lorsque vous arrivez au dernier, et vice versa.  Les principales méthodes du contrôle sont <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> et <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Il n'affiche que des chaînes de texte.  Si vous souhaitez un contrôle qui affiche des valeurs numériques, utilisez le contrôle <xref:System.Windows.Forms.NumericUpDown>.  Pour plus d'informations, consultez [Vue d'ensemble du contrôle NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DomainUpDown>   
 [DomainUpDown, contrôle](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)