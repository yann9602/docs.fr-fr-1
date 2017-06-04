---
title: "Mod&#233;lisation et mappage | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "ESQL"
  - "jsharp"
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 7
---
# Mod&#233;lisation et mappage
Dans [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], vous pouvez définir le modèle conceptuel, le modèle de stockage et le mappage entre les deux de la façon la plus appropriée pour votre application.  Les Outils Entity Data Model dans [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] vous permettent de créer un [fichier .edmx](http://msdn.microsoft.com/fr-fr/f4c8e7ce-1db6-417e-9759-15f8b55155d4) à partir d'une base de données ou un modèle graphique et de mettre à jour ce fichier lorsque la base de données ou le modèle change.  
  
 Depuis Entity Framework 4.1, vous pouvez également créer un modèle par programme à l'aide du développement Code First.  Il existe deux scénarios différents pour le développement Code First.  Dans les deux cas, le développeur définit un modèle lors du codage des définitions de classe .NET Framework, puis spécifie éventuellement un mappage supplémentaire ou une configuration supplémentaire à l'aide des annotations de données ou de l'API Fluent.  
  
 Pour plus d'informations, consultez [Création et mappage d'un modèle conceptuel](http://go.microsoft.com/fwlink/?LinkID=235016).  
  
 Vous pouvez aussi utiliser l'outil EDM Generator, inclus avec le [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].  EdmGen.exe génère les fichiers .csdl, .ssdl et .msl d'une source de données existante.  Vous pouvez également créer manuellement le modèle et mapper le contenu.  Pour plus d'informations, consultez [EDM Generator \(EdmGen.exe\)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).