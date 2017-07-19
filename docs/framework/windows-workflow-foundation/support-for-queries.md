---
title: "Prise en charge des requ&#234;tes | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# Prise en charge des requ&#234;tes
Le magasin d'instances de workflow SQL enregistre un jeu de propriétés connues dans le magasin.Les utilisateurs peuvent demander des instances à partir de ces propriétés.La liste suivante comprend quelques\-unes de ces propriétés connues :  
  
-   **Nom du site.** Nom du site Web qui contient le service.  
  
-   **Chemin d'accès à l'application relatif.** Chemin d'accès à l'application relatif au site Web.  
  
-   **Chemin d'accès au service relatif.** Chemin d'accès au service relatif à l'application.  
  
-   **Nom du service.** Nom porté par le service.  
  
-   **Espace de noms du service.** Nom de l'espace de noms que le service utilise.  
  
-   **Ordinateur actuel.**  
  
-   **Dernier ordinateur**.Ordinateur sur lequel l'instance de service de workflow a été exécutée la dernière fois.  
  
> [!NOTE]
>  Pour les scénarios auto\-hébergés à l'aide de l'hôte du service de workflow, seules les quatre dernières propriétés sont remplies.Pour les scénarios d'application de workflow, seule la dernière propriété est remplie.  
  
 Le runtime du workflow fournit des valeurs pour les trois premières propriétés.L'hôte du service de workflow fournit la valeur pour la propriété **Raison de l'interruption**.Le magasin d'instances de workflow SQL lui\-même fournit des valeurs pour la propriété **Dernier ordinateur mis à jour**.  
  
 La fonctionnalité de magasin d'instances de workflow SQL vous permet également de spécifier les propriétés personnalisées pour lesquelles vous souhaitez stocker les valeurs dans la base de données de persistance et que vous souhaitez utiliser dans les requêtes.Pour plus d'informations sur les promotions personnalisées, consultez [Stocker l'extensibilité](../../../docs/framework/windows-workflow-foundation//store-extensibility.md).  
  
## Vues  
 Le magasin d'instances contient les vues suivantes.Pour plus d'informations, consultez [Schéma de la base de données de persistance](../../../docs/framework/windows-workflow-foundation//persistence-database-schema.md).  
  
### Vue Instances  
 La vue Instances contient les champs suivants :  
  
1.  **Id**  
  
2.  **PendingTimer**  
  
3.  **CreationTime**  
  
4.  **LastUpdatedTime**  
  
5.  **ServiceDeploymentId**  
  
6.  **SuspensionExceptionName**  
  
7.  **SuspensionReason**  
  
8.  **ActiveBookmarks**  
  
9. **CurrentMachine**  
  
10. **LastMachine**  
  
11. **ExecutionStatus**  
  
12. **IsInitialized**  
  
13. **IsSuspended**  
  
14. **IsCompleted**  
  
15. **EncodingOption**  
  
16. **ReadWritePrimitiveDataProperties**  
  
17. **WriteOnlyPrimitiveDataProperties**  
  
18. **ReadWriteComplexDataProperties**  
  
19. **WriteOnlyComplexDataProperties**  
  
### Vue ServiceDeployments  
 La vue ServiceDeployments contient les champs suivants :  
  
1.  **SiteName**  
  
2.  **RelativeServicePath**  
  
3.  **RelativeApplicationPath**  
  
4.  **ServiceName**  
  
5.  **ServiceNamespace**  
  
### Vue InstancePromotedProperties  
 La vue InstancePromotedProperties contient les champs suivants.Pour plus d'informations sur les propriétés promue, consultez la rubrique [Stocker l'extensibilité](../../../docs/framework/windows-workflow-foundation//store-extensibility.md).  
  
1.  **InstanceId**  
  
2.  **EncodingOption**  
  
3.  **PromotionName**  
  
4.  **Value\#** \(une plage de champs comprise entre **Value1** et **Value64**\).