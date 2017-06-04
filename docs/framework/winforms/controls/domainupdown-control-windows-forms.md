---
title: "DomainUpDown, contr&#244;le (Windows Forms) | Microsoft Docs"
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
  - "DomainUpDown (contrôle Windows Forms)"
  - "contrôle toupie"
  - "contrôle toupie, contrôles up-down"
  - "contrôles up-down"
  - "contrôles up-down, contrôles toupie"
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# DomainUpDown, contr&#244;le (Windows Forms)
Le contrôle <xref:System.Windows.Forms.DomainUpDown> Windows Forms se présente comme une zone de texte à laquelle sont associés deux boutons permettant le déplacement vers le haut et vers le bas dans une liste.  Il affiche et définit une chaîne de texte provenant d'une liste d'options.  Pour sélectionner la chaîne, l'utilisateur peut se déplacer dans une liste en cliquant sur des boutons haut et bas, en appuyant sur les touches HAUT et BAS ou en tapant directement une chaîne correspondant à un élément de la liste.  Ce contrôle peut notamment être utilisé pour sélectionner des éléments dans une liste de noms triés par ordre alphabétique  \(pour trier la liste, affectez à la propriété <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> la valeur `true`.\) Ce contrôle a un fonctionnement très proche de celui des zones de liste simples ou déroulantes, mais il occupe un espace plus réduit.  
  
 Les principales propriétés du contrôle sont <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> et <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.  La propriété <xref:System.Windows.Forms.DomainUpDown.Items%2A> contient la liste des objets dont les valeurs du texte sont affichées dans le contrôle.  Si la propriété <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> a la valeur `false`, le contrôle complète automatiquement le texte tapé par l'utilisateur et l'associe à une valeur de la liste.  Si la propriété <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> a la valeur `true`, vous revenez au premier élément de la liste lorsque vous arrivez au dernier, et vice versa.  Les principales méthodes du contrôle sont <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> et <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Il n'affiche que des chaînes de texte.  Si vous souhaitez un contrôle qui affiche des valeurs numériques, utilisez le contrôle <xref:System.Windows.Forms.NumericUpDown>.  Pour plus d'informations, consultez [NumericUpDown, contrôle](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md).  
  
## Dans cette section  
 [Vue d'ensemble du contrôle DomainUpDown](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)  
 Présente les concepts généraux attachés au contrôle <xref:System.Windows.Forms.DomainUpDown>, lequel permet aux utilisateurs de parcourir une liste de chaînes de texte et d'y opérer une sélection.  
  
 [Comment : ajouter par programme des éléments aux contrôles DomainUpDown Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 Explique comment spécifier les chaînes de texte que doit afficher le contrôle <xref:System.Windows.Forms.DomainUpDown>.  
  
 [Comment : supprimer des éléments des contrôles DomainUpDown Windows Forms](../../../../docs/framework/winforms/controls/how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 Explique comment supprimer dans le code des éléments du contrôle <xref:System.Windows.Forms.DomainUpDown>.  
  
## Référence  
 <xref:System.Windows.Forms.DomainUpDown>  
 Décrit cette classe et propose des liens vers tous ses membres.  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 Décrit cette classe et propose des liens vers tous ses membres.  
  
## Rubriques connexes  
 [Contrôles que vous pouvez utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 Fournit la liste complète des contrôles Windows Forms ainsi que des liens vers des informations sur leur utilisation.