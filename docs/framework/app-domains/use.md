---
title: "Utilisation des domaines d&#39;application | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "domaines d’application, à propos de"
  - "Common Language Runtime, domaines d’application"
  - "runtime, domaines d’application"
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# Utilisation des domaines d&#39;application
Les domaines d'application fournissent une unité d'isolation pour le Common Language Runtime.  Ils sont créés et exécutés dans un processus.  Les domaines d'application sont généralement créés par un hôte de runtime, qui est une application responsable du chargement du runtime dans un processus et de l'exécution du code utilisateur dans un domaine d'application.  L'hôte de runtime crée un processus et un domaine d'application par défaut et exécute le code managé dans ce domaine d'application.  Les hôtes de runtime comprennent ASP.NET, Microsoft Internet Explorer et le shell Windows.  
  
 Pour la plupart des applications, vous n'avez pas besoin de créer votre propre domaine d'application ; l'hôte de runtime crée à votre place tout domaine d'application nécessaire.  Toutefois, vous pouvez créer et configurer des domaines d'application supplémentaires si votre application doit isoler du code ou utiliser et décharger des DLL.  
  
## Dans cette section  
 [Comment : créer un domaine d'application](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 Explique comment créer un domaine d'application par programme.  
  
 [Comment : décharger un domaine d'application](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 Explique comment décharger un domaine d'application par programme.  
  
 [Comment : configurer un domaine d'application](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 Propose une introduction à la configuration d'un domaine d'application.  
  
 [Récupération d'informations d'installation à partir d'un domaine d'application](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 Explique comment récupérer des informations d'installation à partir d'un domaine d'application.  
  
 [Comment : charger des assemblys dans un domaine d'application](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 Explique comment charger un assembly dans un domaine d'application.  
  
 [Comment : obtenir des informations relatives au type et aux membres à partir d'un assembly](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Explique comment récupérer des informations sur un assembly.  
  
 [Clichés instantanés d'assemblys](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 Décrit comment les clichés instantanés permettent la mise à jour d'assemblys pendant leur utilisation, et comment configurer les clichés instantanés.  
  
 [Comment : recevoir des notifications des exceptions de première chance](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 Explique comment vous pouvez recevoir la notification qu'une exception a été levée, avant que le Common Language Runtime n'ait commencé à rechercher des gestionnaires d'exceptions.  
  
 [Résolution des chargements d'assemblys](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 Fournit des conseils sur l'utilisation de l'événement <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> pour résoudre des échecs de chargement de l'assembly.  
  
## Référence  
 <xref:System.AppDomain>  
 Représente un domaine d'application.  Fournit des méthodes destinées à créer et à contrôler des domaines d'application.  
  
## Rubriques connexes  
 [Assemblys dans le Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Propose une vue d'ensemble des fonctions exécutées par les assemblys.  
  
 [Programmation à l'aide d'assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 Décrit comment créer et signer des assemblys et leur affecter des attributs.  
  
 [Émission d'assemblys et de méthodes dynamiques](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 Décrit comment créer des assemblys dynamiques.  
  
 [Domaines d'application](../../../docs/framework/app-domains/application-domains.md)  
 Fournit une vue d'ensemble conceptuelle des domaines d'application.  
  
 [Vue d'ensemble de la réflexion](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Explique comment utiliser la classe **Reflection** pour obtenir des informations sur un assembly.