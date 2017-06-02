---
title: "&#201;mission d&#39;assemblys et de m&#233;thodes dynamiques | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "assemblys (.NET Framework), émettre des assemblys dynamiques"
  - "assemblys dynamiques"
  - "métadonnées, créer des interfaces"
  - "émission de réflexion"
  - "émission de réflexion, vue d'ensemble"
ms.assetid: 8e8e2631-62fd-40e7-a8ee-0039b06749bc
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# &#201;mission d&#39;assemblys et de m&#233;thodes dynamiques
Cette section décrit un ensemble de types managés dans l'espace de noms <xref:System.Reflection.Emit>, qui permettent à un compilateur ou à un outil d'émettre des métadonnées et du langage MSIL \(Microsoft Intermediate Language\) au moment de l'exécution et de générer éventuellement un fichier exécutable portable sur le disque.  Les moteurs de script et les compilateurs sont les principaux utilisateurs de cet espace de noms.  Dans cette section, la fonctionnalité fournies par l'espace de noms <xref:System.Reflection.Emit> est appelée émission de réflexion.  
  
 L'émission de réflexion offre les possibilités suivantes :  
  
-   Définir des méthodes globales légères au moment de l'exécution à l'aide de la classe <xref:System.Reflection.Emit.DynamicMethod>, et les exécuter à l'aide de délégués.  
  
-   Définir des assemblys au moment de l'exécution, puis les exécuter et\/ou les enregistrer sur disque.  
  
-   Définir des assemblys au moment de l'exécution, les exécuter, puis les décharger et autoriser le garbage collection à libérer leurs ressources.  
  
-   Définir des modules dans de nouveaux assemblys au moment de l'exécution, puis les exécuter et\/ou les enregistrer sur disque.  
  
-   Définir des types dans des modules au moment de l'exécution, créer des instances de ces types et appeler leurs méthodes.  
  
-   Définir des informations symboliques pour des modules définis, qui peut être utilisées par des outils comme des débogueurs et des profileurs de code.  
  
 En plus des types managés dans l'espace de noms <xref:System.Reflection.Emit>, il existe des interfaces de métadonnées non managées qui sont décrites dans la documentation de référence [Interfaces de métadonnées](../../../ocs/framework/unmanaged-api/metadata/metadata-interfaces.md).  L'émission de réflexion managée offre une vérification des erreurs sémantiques plus puissante et un niveau d'abstraction des métadonnées plus élevé que les interfaces de métadonnées non managées.  
  
 Une autre ressource utile pour travailler avec les métadonnées et MSIL est la documentation de la Common Language Infrastructure \(CLI\), en particulier "Partie II : définition et sémantique des métadonnées" et "Partie III : jeu d'instructions de CIL".  La documentation est disponible en ligne sur [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) et sur le [site web Ecma](http://go.microsoft.com/fwlink/?LinkId=116487).  
  
## Dans cette section  
 [Problèmes de sécurité dans l'émission de réflexion](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
 Décrit les problèmes de sécurité liés à la création d'assemblys dynamiques en utilisant l'émission de réflexion.  
  
## Référence  
 <xref:System.Reflection.Emit.OpCodes>  
 Répertorie les codes des instructions MSIL que vous pouvez utiliser pour créer des corps de méthode.  
  
 <xref:System.Reflection.Emit>  
 Contient des classes managées utilisées pour émettre des méthodes, des assemblys et des types dynamiques.  
  
 <xref:System.Type>  
 Décrit la classe <xref:System.Type>, qui représente des types dans la réflexion managée et dans l'émission de réflexion, et qui est essentielle dans l'utilisation de ces technologies.  
  
 <xref:System.Reflection>  
 Contient des classes managées utilisées pour explorer les métadonnées et le code managé.  
  
## Rubriques connexes  
 [Réflexion](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Explique comment explorer les métadonnées et le code managé.  
  
 [Assemblys dans le Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Donne une vue d'ensemble des assemblys dans le .NET Framework.