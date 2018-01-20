---
title: "Sécurité des Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designer access security [Windows Forms]
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms]
- access control [Windows Forms], Windows Forms
- security policy [Windows Forms], Windows Forms
ms.assetid: 932d438a-5285-46d8-a958-8c93d0ad6cae
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8bd9b87fdfa54a6f9bf53e4fa897106257b4c625
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="windows-forms-security"></a>Sécurité des Windows Forms
Windows Forms comprend un modèle de sécurité qui est basée sur code (niveaux de sécurité sont définis pour le code, quel que soit l’utilisateur qui exécute le code). Il s’agit en plus de tous les schémas de sécurité qui peuvent être déjà en place sur votre système. Celles-ci peuvent inclure dans le navigateur (telles que la sécurité basée sur la zone disponible dans Internet Explorer) ou le système d’exploitation (par exemple, la sécurité basée sur les informations d’identification de Windows NT).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble de la sécurité dans les Windows Forms](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 Présente brièvement le modèle de sécurité .NET Framework et les étapes de base nécessaires pour les Windows Forms dans votre application.  
  
 [Accès plus sécurisé aux fichiers et aux données dans les Windows Forms](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 Décrit comment accéder aux fichiers et des données dans un environnement de confiance partiel.  
  
 [Impression plus sécurisée dans les Windows Forms](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 Décrit comment accéder aux fonctionnalités d’impression dans un environnement de confiance partiel.  
  
 [Considérations supplémentaires sur la sécurité des Windows Forms](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 Décrit comment manipuler des fenêtres, l’utilisation du Presse-papiers et effectuer des appels au code non managé dans un environnement de confiance partiel.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [NIB : Stratégie de sécurité par défaut](http://msdn.microsoft.com/library/2c086873-0894-4f4d-8f7e-47427c1a3b55)  
 Répertorie les autorisations par défaut accordées dans les jeux d’autorisations confiance totale, Intranet Local et Internet.  
  
 [NIB : Administration de stratégie de sécurité générale](http://msdn.microsoft.com/library/5121fe35-f0e3-402c-94ab-4f35b0a87b4b)  
 Fournit des informations sur l’administration de la stratégie de sécurité .NET Framework et l’élévation des autorisations.  
  
 [Autorisations dangereuses et Administration de la stratégie](../../../docs/framework/misc/dangerous-permissions-and-policy-administration.md)  
 Présente certaines autorisations du.NET Framework susceptibles de permettre le contournement du système de sécurité.  
  
 [Instructions de codage sécurisé](../../../docs/standard/security/secure-coding-guidelines.md)  
 Liens vers des rubriques qui expliquent les meilleures pratiques pour en toute sécurité l’écriture de code par rapport à .NET Framework.  
  
 [NIB : Demande d’autorisations](http://msdn.microsoft.com/library/0447c49d-8cba-45e4-862c-ff0b59bebdc2)  
 Décrit l’utilisation d’attributs pour permettre au runtime de savoir quelles autorisations que votre code doit s’exécuter.  
  
 [Concepts fondamentaux sur la sécurité](../../../docs/standard/security/key-security-concepts.md)  
 Liens vers des rubriques qui couvrent les aspects de sécurité du code base.  
  
 [Notions fondamentales de la sécurité d’accès du code](../../../docs/framework/misc/code-access-security-basics.md)  
 Décrit les principes fondamentaux de l’utilisation de la stratégie de sécurité du .NET Framework.  
  
 [NIB : Déterminer le moment modifier la stratégie de sécurité](http://msdn.microsoft.com/library/af749b17-e461-409d-84b9-a3d44789db16)  
 Explique comment déterminer quand vos applications doivent diverger de la stratégie de sécurité par défaut.  
  
 [NIB : Déploiement de stratégie de sécurité](http://msdn.microsoft.com/library/f936c1e5-033b-4bd9-a3bd-a39ba733a681)  
 Décrit la méthode la mieux adaptée pour déployer les modifications de stratégie de sécurité.
