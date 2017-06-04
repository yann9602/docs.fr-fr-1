---
title: "S&#233;curit&#233; des Windows Forms | Microsoft Docs"
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
  - "contrôle d'accès, Windows Forms"
  - "sécurité de l'accès au concepteur"
  - "autorisations, Windows Forms"
  - "sécurité (Windows Forms)"
  - "stratégie de sécurité, Windows Forms"
  - "Windows Forms, sécurité"
ms.assetid: 932d438a-5285-46d8-a958-8c93d0ad6cae
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# S&#233;curit&#233; des Windows Forms
Les Windows Forms présentent un modèle de sécurité basé sur le code \(des niveaux de sécurité sont définis pour le code, quel que soit l'utilisateur qui exécute ce dernier\).  Ce modèle vient s'ajouter aux éventuels schémas de sécurité déjà en place sur le système informatique.  Ces schémas peuvent notamment provenir du navigateur \(sécurité par zone disponible dans Internet Explorer\) ou du système d'exploitation \(sécurité avec informations d'identification de Windows NT\).  
  
## Dans cette section  
 [Vue d'ensemble de la sécurité dans les Windows Forms](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 Présente brièvement le modèle de sécurité .NET Framework et les étapes élémentaires nécessaires pour garantir la sécurité des Windows Forms dans votre application.  
  
 [Accès plus sécurisé aux fichiers et aux données dans les Windows Forms](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 Explique comment accéder aux fichiers et aux données dans un environnement de niveau de confiance partiel.  
  
 [Impression plus sécurisée dans les Windows Forms](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 Explique comment accéder aux fonctionnalités d'impression dans un environnement de niveau de confiance partiel.  
  
 [Considérations supplémentaires sur la sécurité des Windows Forms](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 Explique comment manipuler des fenêtres, utiliser le Presse\-papiers et appeler du code non managé dans un environnement de niveau de confiance partiel.  
  
## Rubriques connexes  
 [NIB: Default Security Policy](http://msdn.microsoft.com/fr-fr/2c086873-0894-4f4d-8f7e-47427c1a3b55)  
 Répertorie les autorisations par défaut accordées dans les jeux d'autorisations Confiance totale, Intranet local et Internet.  
  
 [NIB: General Security Policy Administration](http://msdn.microsoft.com/fr-fr/5121fe35-f0e3-402c-94ab-4f35b0a87b4b)  
 Fournit des informations sur l'administration de la stratégie de sécurité du .NET Framework et l'élévation des autorisations.  
  
 [Autorisations dangereuses et administration de stratégie](../../../docs/framework/misc/dangerous-permissions-and-policy-administration.md)  
 Présente certaines autorisations du .NET Framework susceptibles de permettre le contournement du système de sécurité.  
  
 [Instructions de codage sécurisé](../../../docs/standard/security/secure-coding-guidelines.md)  
 Fournit des liens vers des rubriques expliquant les méthodes conseillées pour écrire du code en toute sécurité dans le .NET Framework.  
  
 [NIB: Requesting Permissions](http://msdn.microsoft.com/fr-fr/0447c49d-8cba-45e4-862c-ff0b59bebdc2)  
 Traite de l'utilisation d'attributs pour informer le runtime des autorisations requises par le code pour être exécuté.  
  
 [Concepts fondamentaux sur la sécurité](../../../docs/standard/security/key-security-concepts.md)  
 Fournit des liens vers des rubriques traitant des bases de la sécurité du code.  
  
 [Notions fondamentales de la sécurité d'accès du code](../../../docs/framework/misc/code-access-security-basics.md)  
 Présente les concepts de base de l'utilisation de la stratégie de sécurité du runtime du .NET Framework.  
  
 [NIB: Determining When to Modify Security Policy](http://msdn.microsoft.com/fr-fr/af749b17-e461-409d-84b9-a3d44789db16)  
 Explique comment déterminer le moment auquel vos applications doivent diverger de la stratégie de sécurité par défaut.  
  
 [NIB: Deploying Security Policy](http://msdn.microsoft.com/fr-fr/f936c1e5-033b-4bd9-a3bd-a39ba733a681)  
 Traite de la méthode la mieux adaptée pour déployer les modifications de la stratégie de sécurité.