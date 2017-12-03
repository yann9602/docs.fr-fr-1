---
title: "Création d'activités de contrôle de flux personnalisées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27f409f6-2d1d-4cfb-9765-93eb2ad667d5
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5a2a45f0b923c9f30bb8df1c59be54e00d844551
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="creating-custom-flow-control-activities"></a>Création d'activités de contrôle de flux personnalisées
Le .Net Framework contient diverses activités de contrôle de flux dont le fonctionnement est similaire à celui de structures de programmation abstraite (telles que <xref:System.Activities.Statements.Flowchart>) ou aux instructions de programmation standard (telles que <xref:System.Activities.Statements.If>). Cette rubrique décrit l’architecture de l’un des exemples de projets, [ForEach Non générique](../../../docs/framework/windows-workflow-foundation/samples/non-generic-foreach.md).  
  
## <a name="creating-the-custom-class"></a>Création de la classe personnalisée  
 Étant donné que la classe ForEach non générique devra planifier des activités enfants, elle devra dériver de <xref:System.Activities.NativeActivity>, puisque les activités qui dérivent de <xref:System.Workflow.Activities.CodeActivity> ne disposent pas de cette fonctionnalité.  
  
```  
public sealed class ForEach : NativeActivity  
    {  
```  
  
 La classe personnalisée requiert que plusieurs membres stockent les données utilisées par l'activité et fournissent des fonctionnalités permettant d'exécuter les activités enfants de l'activité. Ces membres incluent :  
  
-   `valueEnumerator` : la <xref:System.Activities.Variable%601> non publique de type <xref:System.Collections.IEnumerator> utilisée pour itérer sur les collections d'éléments. Ce membre est de type <xref:System.Activities.Variable%601>, car il est utilisé en interne dans l'activité, plutôt qu'un argument ou une propriété publique, qui serait utilisé si cet objet avait une origine externe à l'activité.  
  
-   `OnChildComplete` : la propriété <xref:System.Activities.CompletionCallback> publique exécutée lorsque chaque enfant termine l'exécution. Ce membre est défini comme une propriété CLR, puisque sa valeur ne changera pas dans les différentes instances de l'activité.  
  
-   `Values` : la collection d'entrées utilisée pour les itérations de l'activité enfant. Ce membre est de type <xref:System.Activities.InArgument%601>, puisque l'origine des données est extérieure à l'activité, mais le contenu des collection n'est pas supposé changer au cours de l'exécution de l'activité. Si l'activité nécessitait que la fonctionnalité modifie le contenu de cette collection au cours de l'exécution de l'activité (pour ajouter ou supprimer des activités, par exemple), ce membre aurait été défini comme <xref:System.Activities.ActivityAction>, qui aurait ensuite été évalué lors de chaque accès, de sorte que l'activité ait accès aux modifications.  
  
-   `Body` : ce membre définit l'activité à exécuter pour chaque élément de la collection `Values`. Ce membre est défini comme <xref:System.Activities.ActivityAction> de sorte qu'il est évalué chaque fois qu'on y accède.  
  
-   `Execute` : cette méthode utilise les membres non publics `InternalExecute`, `OnForEachComplete` et `GetStateAndExecute` pour planifier l'exécution et assigner le gestionnaire d'achèvement de l'activité enfant défini dans le membre de corps.  
  
-   `CacheMetadata` : ce membre fournit au runtime les informations dont il a besoin pour exécuter l'activité. Par défaut, la méthode `CacheMetadata` d'une activité indique au runtime tous les membres publics de l'activité, mais puisque cette activité utilise des membres privés pour certaines fonctionnalités, elle doit signaler leur existence au runtime de telle sorte qu'il en soit informé. Dans ce cas, la fonction `CacheMetadata` est remplacée afin que le membre `valueEnumerator` soit accessible. Ce membre crée également un argument pour les valeurs de l'activité afin qu'elles puissent être passées dans l'activité au cours de l'exécution.
