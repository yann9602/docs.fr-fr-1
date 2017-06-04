---
title: "Propri&#233;t&#233;s des contr&#244;les Windows Forms que prennent en charge les instructions relatives &#224; l&#39;accessibilit&#233; | Microsoft Docs"
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
  - "accessibilité, propriétés de contrôle Windows Forms"
  - "Windows Forms, propriétés d'accessibilité des contrôles"
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Propri&#233;t&#233;s des contr&#244;les Windows Forms que prennent en charge les instructions relatives &#224; l&#39;accessibilit&#233;
De nombreuses règles d'accessibilité sont prises en charge par des contrôles de la boîte à outils standard des Windows Forms, en particulier l'exposition du focus clavier et celle des éléments de l'écran.  
  
## Planification de l'accessibilité  
 Les propriétés des contrôles peuvent être utilisées pour prendre en charge d'autres règles d'accessibilité, comme le montre le tableau suivant.  En outre, vous devez utiliser des menus pour offrir un accès aux fonctionnalités du programme.  
  
|Propriété du contrôle|Considérations d'accessibilité|  
|---------------------------|------------------------------------|  
|AccessibleDescription|La description est indiquée aux outils d'accessibilité tels que les lecteurs d'écran.  Les outils d'accessibilité sont des programmes et des appareils spécialisés qui aident les personnes atteintes d'un handicap à se servir plus efficacement d'un ordinateur.|  
|AccessibleName|Le nom qui est indiqué aux outils d'accessibilité.|  
|AccessibleRole|Décrit l'usage qui est réservé à l'élément dans l'interface utilisateur.|  
|TabIndex|Crée un chemin de navigation cohérent dans le formulaire.  Dans le cas des contrôles sans étiquette intrinsèque \(zones de texte, par exemple\), il est important que l'étiquette qui leur est associée les précède immédiatement dans l'ordre de tabulation.|  
|Texte|Utilisez le caractère « & » pour créer des touches d'accès rapide.  L'accès clavier documenté aux fonctionnalités est assuré en partie par les touches d'accès rapide.|  
|Font Size|Si la taille de la police n'est pas réglable, elle doit avoir la valeur 10 points ou plus.  Une fois que la taille de la police est définie dans le formulaire, tous les contrôles qui seront ajoutés au formulaire par la suite auront cette taille.|  
|Forecolor|Si cette propriété prend la valeur par défaut, les préférences de couleur de l'utilisateur seront utilisées dans le formulaire.|  
|BackColor|Si cette propriété prend la valeur par défaut, les préférences de couleur de l'utilisateur seront utilisées dans le formulaire.|  
|BackgroundImage|Il est conseillé de laisser cette propriété vide pour améliorer la lisibilité du texte.|  
  
## Voir aussi  
 [Procédure pas à pas : création d'une application Windows accessible](../../../../docs/framework/winforms/advanced/walkthrough-creating-an-accessible-windows-based-application.md)