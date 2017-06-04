---
title: "&lt;commonBehaviors&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;commonBehaviors&gt;
La section `commonBehaviors` peut uniquement être définie dans le fichier machine.config.  Elle définit deux collections enfants nommées `endpointBehaviors` et `serviceBehaviors`.  Chaque collection définit des éléments de comportement consommés respectivement par tous les points de terminaison et services de [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] sur l'ordinateur.  Les comportements définis dans `endpointBehaviors` sont appliqués uniquement aux clients et les comportements définis dans `serviceBehaviors` s'appliquent uniquement aux services.  Si un comportement est défini dans les sections `commonBehaviors` et `behaviors`, le comportement dans la section `behaviors` a la préférence.