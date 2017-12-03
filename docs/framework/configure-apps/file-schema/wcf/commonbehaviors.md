---
title: '&lt;commonBehaviors&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06d09763b0281eb7edafadbbd59ff924b751d73e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcommonbehaviorsgt"></a><span data-ttu-id="74a4d-102">&lt;commonBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="74a4d-102">&lt;commonBehaviors&gt;</span></span>
<span data-ttu-id="74a4d-103">La section `commonBehaviors` peut uniquement être définie dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="74a4d-103">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="74a4d-104">Elle définit deux collections enfants nommées `endpointBehaviors` et `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="74a4d-104">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="74a4d-105">Chaque collection définit des éléments de comportement consommés respectivement par tous les points de terminaison et services de [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="74a4d-105">Each collection defines behavior elements consumed by all [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] endpoints and services on the machine respectively.</span></span> <span data-ttu-id="74a4d-106">Les comportements définis dans `endpointBehaviors` sont appliqués uniquement aux clients et les comportements définis dans `serviceBehaviors` s'appliquent uniquement aux services.</span><span class="sxs-lookup"><span data-stu-id="74a4d-106">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="74a4d-107">Si un comportement est défini dans les sections `commonBehaviors` et `behaviors`, le comportement dans la section `behaviors` a la préférence.</span><span class="sxs-lookup"><span data-stu-id="74a4d-107">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
