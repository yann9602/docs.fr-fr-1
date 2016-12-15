---
title: "Avertissement du compilateur (niveau&#160;1) CS1697 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1697"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1697"
ms.assetid: 0cd931b7-f358-4ff0-b441-27668645d7d5
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS1697
Différentes valeurs de somme de contrôle sont données pour 'file name'  
  
 Vous avez spécifié plusieurs sommes de contrôle pour un fichier donné. Le débogueur utilise la valeur de la somme de contrôle pour déterminer le fichier à déboguer quand plusieurs fichiers portent le même nom dans un projet. La plupart des utilisateurs n’obtiennent pas cette erreur, mais si vous écrivez une application qui génère du code, vous risquez de la rencontrer. Pour résoudre cette erreur, assurez\-vous de générer une seule fois la somme de contrôle pour le fichier de code donné.