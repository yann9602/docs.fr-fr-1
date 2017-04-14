---
title: "Programmation &#224; l&#39;aide de domaines d&#39;application et d&#39;assemblys | Microsoft Docs"
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
  - "domaines d'application, programmation"
  - "assemblys (.NET Framework), programmation"
  - "programmer des domaines d'application"
  - "programmer des assemblys"
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Programmation &#224; l&#39;aide de domaines d&#39;application et d&#39;assemblys
Les hôtes tels que Microsoft Internet Explorer, ASP.NET et le shell Windows chargent le Common Language Runtime dans un processus, créent un [domaine d'application](../../../docs/framework/app-domains/application-domains.md) dans ce processus, puis chargent et exécutent le code utilisateur dans ce domaine d'application lors de l'exécution d'une application .NET Framework.  Dans la plupart des cas, vous n'avez pas à vous préoccuper de la création de domaines d'application ni du chargement d'assemblys dans ces domaines, car ces tâches sont réalisées par l'hôte de runtime.  
  
 Cependant, si vous créez une application devant héberger le Common Language Runtime, si vous créez des outils ou du code que vous souhaitez décharger par programme ou si vous créez des composants enfichables pouvant être déchargés et rechargés à la volée, vous créerez vos propres domaines d'application.  Cette section fournit des informations importantes sur l'utilisation des domaines d'application et des assemblys chargés dans ces domaines, qui vous seront utiles même si vous ne créez pas d'hôte de runtime.  
  
## Dans cette section  
 [Rubriques Comment relatives aux domaines d'application et aux assemblys](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 Fournit des liens vers toutes les rubriques "Comment" de la documentation conceptuelle relative à la programmation à l'aide des domaines d'application et des assemblys.  
  
 [Utilisation des domaines d'application](../../../docs/framework/app-domains/use.md)  
 Fournit des exemples de création, configuration et utilisation de domaines d'application.  
  
 [Programmation à l'aide d'assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 Décrit comment créer et signer des assemblys et leur affecter des attributs.  
  
## Rubriques connexes  
 [Émission d'assemblys et de méthodes dynamiques](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 Décrit comment créer des assemblys dynamiques.  
  
 [Assemblys dans le Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Fournit une vue d'ensemble conceptuelle des assemblys.  
  
 [Domaines d'application](../../../docs/framework/app-domains/application-domains.md)  
 Fournit une vue d'ensemble conceptuelle des domaines d'application.  
  
 [Vue d'ensemble de la réflexion](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Explique comment utiliser la classe **Reflection** pour obtenir des informations sur un assembly.