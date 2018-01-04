---
title: "Inspection d'arborescence d'activité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 100d00e4-8c1d-4233-8fbb-dd443a01155d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: efb7f8f1603de67f21aee7e1746670e324d5e238
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="activity-tree-inspection"></a>Inspection d'arborescence d'activité
Les auteurs de l’application de workflow utilisent l’inspection de l’arborescence d’activité pour inspecter les flux de travail hébergés par l’application. En utilisant l'objet <xref:System.Activities.WorkflowInspectionServices>, il est possible de rechercher des activités enfants particulières dans les flux de travail, chaque activité et ses propriétés peuvent être énumérées et les métadonnées de runtime relatives aux activités peuvent être mises en cache à une heure spécifique. Cette rubrique fournit une vue d'ensemble de l'objet <xref:System.Activities.WorkflowInspectionServices> et de son mode d'utilisation pour inspecter une arborescence d'activité.  
  
## <a name="using-workflowinspectionservices"></a>Utilisation de WorkflowInspectionServices  
 La méthode <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> est utilisée pour énumérer toutes les activités dans l'arborescence d'activité spécifiée. <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> retourne un énumérable qui touche toutes les activités de l'arborescence, dont les enfants, les gestionnaires des délégués, les valeurs par défaut des variables et les expressions d'arguments. Dans l'exemple suivant, une définition de workflow est créée à l'aide d'un <xref:System.Activities.Statements.Sequence>, d'un <xref:System.Activities.Statements.While>, d'un <xref:System.Activities.Statements.ForEach%601>, d'un <xref:System.Activities.Statements.WriteLine> et d'expressions. Une fois la définition de workflow créée, elle est appelée, puis la méthode `InspectActivity` est appelée.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#45](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#45)]  
  
 Pour énumérer les activités, <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> est appelé sur l'activité racine, et à nouveau, de façon récursive, sur chaque activité retournée. Dans l'exemple suivant, la propriété <xref:System.Activities.Activity.DisplayName%2A> de chaque activité et expression dans l'arborescence d'activité est écrite dans la console.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#46](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#46)]  
  
 Cet exemple de code génère la sortie suivante :  
  
 **Élément de liste 1**  
**Élément de liste 2**   
**Élément de liste 3**   
**Élément de liste 4**   
**Élément de liste 5**   
**Éléments ajoutés à la collection.**   
**Séquence**   
 **Littéral < liste\<chaîne >>**  
 **While**  
 **AddToCollection\<chaîne >**  
 **VariableValue < ICollection\<chaîne >>**  
 **LambdaValue\<chaîne >**  
 **LocationReferenceValue < liste\<chaîne >>**  
 **LambdaValue\<booléenne >**  
 **LocationReferenceValue < liste\<chaîne >>**  
 **ForEach\<chaîne >**  
 **VariableValue < IEnumerable\<chaîne >>**  
 **WriteLine**  
 **DelegateArgumentValue\<chaîne >**  
 **Séquence**  
 **WriteLine**  
 **Littéral\<chaîne >** pour récupérer une activité spécifique au lieu d’énumérer toutes les activités, <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> est utilisé. Les méthodes <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> et <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> effectuent toutes les deux une mise en cache des métadonnées si `WorkflowInspectionServices.CacheMetadata` n'a pas été appelé précédemment. Si la méthode <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> a été appelée, la méthode <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> est basée sur les métadonnées existantes. Par conséquent, si l'arborescence a été modifiée depuis le dernier appel à la méthode <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A>, la méthode <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> peut provoquer des résultats inattendus. Si les modifications ont été apportées au flux de travail après l’appel <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A>, métadonnées peuvent être remis en cache en appelant le <xref:System.Activities.Validation.ActivityValidationServices> <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> (méthode). La section suivante traite de la mise en cache des métadonnées.  
  
### <a name="caching-metadata"></a>Mise en cache des métadonnées  
 La mise en cache des métadonnées pour une activité génère et valide une description des arguments, variables, activités enfants et délégués d'activité de l'activité en question. Par défaut, le runtime met en cache les métadonnées lorsqu'une activité est prête à être exécutée. Si un auteur hôte du workflow souhaite mettre préalablement en cache les métadonnées pour une activité ou arborescence d'activité, par exemple pour payer d'avance la totalité du coût, la méthode <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> peut servir à mettre en cache les métadonnées à l'heure souhaitée.
