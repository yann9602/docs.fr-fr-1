---
title: "assemblys et ex&#233;cution c&#244;te &#224; c&#244;te | Microsoft Docs"
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
  - "assemblys (.NET Framework), exécution côte à côte"
  - "exécution côte à côte (.NET Framework)"
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# assemblys et ex&#233;cution c&#244;te &#224; c&#244;te
L'exécution côte à côte consiste à stocker et exécuter plusieurs versions d'une application ou d'un composant sur un même ordinateur.  Cela signifie que peuvent coexister simultanément sur un même ordinateur plusieurs versions du runtime ainsi que plusieurs versions d'applications et de composants utilisant une version du runtime.  L'exécution côte à côte vous offre un meilleur contrôle des versions auxquelles peut être liée une application ainsi que de la version du runtime utilisée par une application.  
  
 La prise en charge du stockage et de l'exécution côte à côte de différentes versions du même assembly fait partie intégrante de l'attribution des noms forts et se trouve intégrée à l'infrastructure du runtime.  Comme le numéro de version de l'assembly avec nom fort fait partie de son identité, le runtime peut stocker plusieurs versions du même assembly dans le Global Assembly Cache et charger ces assemblys au moment de l'exécution.  
  
 Bien que le runtime vous permette de créer des applications côte à côte, l'exécution côte à côte n'est pas automatique.  Pour plus d'informations sur la création d'applications pour l'exécution côte à côte, consultez [Indications pour la création de composants pour l'exécution côte à côte](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## Voir aussi  
 [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [Assemblys dans le Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)