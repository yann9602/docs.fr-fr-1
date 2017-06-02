---
title: "Modifications de s&#233;curit&#233; dans le&#160;.NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "APTCA (attribut)"
  - ".NET Framework 4, modifications de sécurité"
  - "sécurité du .NET Framework"
  - "code transparent de sécurité"
  - "code critique de sécurité"
  - "sécurité d’accès du code, modifications"
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
caps.latest.revision: 52
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 52
---
# Modifications de s&#233;curit&#233; dans le&#160;.NET Framework
L'évolution la plus importante sur le plan de la sécurité dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] est l'utilisation de noms forts. Pour obtenir une description de ces modifications, consultez [Amélioration de l'utilisation de noms forts](../../../docs/framework/app-domains/enhanced-strong-naming.md).  
  
 Le .NET Framework fournit un modèle de sécurité à deux niveaux pour les applications managées. Les applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] s'exécutent dans un conteneur de sécurité Windows qui limite l'accès aux ressources. Dans ce conteneur, les applications managées s'exécutent en mode confiance totale. Du point de vue de la sécurité d'accès du code \(CAS\), un développeur ne peut rien faire pour élever les privilèges. Pour plus d’informations sur les privilèges octroyés par Windows, consultez [Déclarations des fonctionnalités d’application \(applications du Windows Store\)](http://go.microsoft.com/fwlink/?LinkId=230436) dans le centre de développement Windows. Pour plus d’informations sur la création d’une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], consultez [Créer votre première application Windows Runtime en C\# ou Visual Basic](http://go.microsoft.com/fwlink/?LinkId=230461).