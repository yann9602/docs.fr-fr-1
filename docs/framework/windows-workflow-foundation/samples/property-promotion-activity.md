---
title: "Activité de promotion de propriétés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 802196b7-1159-4c05-b41b-d3bfdfcc88d9
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bd8356927ad7cb4c24cc278fcb901cc543c6d7b5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="property-promotion-activity"></a><span data-ttu-id="c0081-102">Activité de promotion de propriétés</span><span class="sxs-lookup"><span data-stu-id="c0081-102">Property Promotion Activity</span></span>
<span data-ttu-id="c0081-103">Cet exemple fournit une solution de bout en bout qui intègre la fonctionnalité Promotion de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> directement dans l'interface de création de workflow.</span><span class="sxs-lookup"><span data-stu-id="c0081-103">This sample provides an end-to-end solution that integrates the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Promotion feature directly into the workflow authoring experience.</span></span> <span data-ttu-id="c0081-104">Une collection d'éléments de configuration, des activités de workflow et des extensions de workflow qui simplifient l'utilisation de la fonctionnalité Promotion sont fournies.</span><span class="sxs-lookup"><span data-stu-id="c0081-104">A collection of configuration elements, workflow activities, and workflow extensions that simplify the use of the Promotion feature are provided.</span></span> <span data-ttu-id="c0081-105">En outre, l'exemple contient un workflow simple qui montre comment utiliser cette collection.</span><span class="sxs-lookup"><span data-stu-id="c0081-105">Additionally, the sample contains a simple workflow that demonstrates how to use this collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0081-106">Les exemples sont fournis à titre éducatif uniquement.</span><span class="sxs-lookup"><span data-stu-id="c0081-106">Samples are provided for educational purposes only.</span></span> <span data-ttu-id="c0081-107">Ils ne sont pas destinés à être utilisés dans un environnement de production et n'ont pas été testés à cet usage.</span><span class="sxs-lookup"><span data-stu-id="c0081-107">They are not intended for a production environment, and have not been tested in a production environment.</span></span> <span data-ttu-id="c0081-108">Microsoft ne fournit aucun support technique pour ces exemples.</span><span class="sxs-lookup"><span data-stu-id="c0081-108">Microsoft does not provide technical support for these samples.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c0081-109">Composants requis</span><span class="sxs-lookup"><span data-stu-id="c0081-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="c0081-110">Base de données <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> initialisée</span><span class="sxs-lookup"><span data-stu-id="c0081-110">An initialized <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> database</span></span>  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]  
  
## <a name="sample-projects"></a><span data-ttu-id="c0081-111">Exemples de projet</span><span class="sxs-lookup"><span data-stu-id="c0081-111">Sample Projects</span></span>  
  
-   <span data-ttu-id="c0081-112">Le **PropertyPromotionActivity** projet contient des fichiers pour les éléments de configuration spécifiques à la promotion, activités de workflow et extensions de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="c0081-112">The **PropertyPromotionActivity** project contains files pertaining to the promotion-specific configuration elements, workflow activities, and workflow extensions.</span></span>  
  
-   <span data-ttu-id="c0081-113">Le **CounterServiceApplication** projet contient un exemple de workflow qui utilise le **SqlWorkflowInstanceStorePromotion** projet.</span><span class="sxs-lookup"><span data-stu-id="c0081-113">The **CounterServiceApplication** project contains a sample workflow that uses the **SqlWorkflowInstanceStorePromotion** project.</span></span>  
  
-   <span data-ttu-id="c0081-114">Script SQL (PropertyPromotionActivitySQLSample.sql) qui doit être exécuté sur la base de données <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>.</span><span class="sxs-lookup"><span data-stu-id="c0081-114">A SQL script (PropertyPromotionActivitySQLSample.sql) that must be run against the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> database.</span></span>  
  
-   <span data-ttu-id="c0081-115">Un fichier solution qui lie les deux projets [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] (`PropertyPromotionActivity.sln`)</span><span class="sxs-lookup"><span data-stu-id="c0081-115">A solution file that links the two [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] projects (`PropertyPromotionActivity.sln`)</span></span>  
  
## <a name="to-set-up-and-run-the-sample"></a><span data-ttu-id="c0081-116">Pour configurer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="c0081-116">To set up and run the sample</span></span>  
  
1.  <span data-ttu-id="c0081-117">Initialisez une base de données de persistance de workflow.</span><span class="sxs-lookup"><span data-stu-id="c0081-117">Initialize a workflow persistence database.</span></span>  
  
    1.  <span data-ttu-id="c0081-118">Accédez au répertoire de l'exemple (\WF\Basic\Persistence\PropertyPromotionActivity) et exécutez CreateInstanceStore.cmd.</span><span class="sxs-lookup"><span data-stu-id="c0081-118">Navigate to the sample directory (\WF\Basic\Persistence\PropertyPromotionActivity) and run CreateInstanceStore.cmd.</span></span>  
  
    2.  <span data-ttu-id="c0081-119">Si les privilèges d'administrateur ne sont pas disponibles, créez une connexion SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c0081-119">If Administrator privileges are not available, create a SQL Server login.</span></span> <span data-ttu-id="c0081-120">Dans SQL Server Management Studio, accédez à **sécurité**, **connexions**.</span><span class="sxs-lookup"><span data-stu-id="c0081-120">In SQL Server Management Studio, go to **Security**, **Logins**.</span></span> <span data-ttu-id="c0081-121">Avec le bouton droit **connexions** et créez une nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="c0081-121">Right-click **Logins** and create a new login.</span></span> <span data-ttu-id="c0081-122">Ajoutez votre utilisateur ACL au rôle SQL en ouvrant **bases de données**, **InstanceStore**, **sécurité**.</span><span class="sxs-lookup"><span data-stu-id="c0081-122">Add your ACL user to the SQL role by opening **Databases**, **InstanceStore**, **Security**.</span></span> <span data-ttu-id="c0081-123">Avec le bouton droit **utilisateurs** et sélectionnez **nouvel utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="c0081-123">Right-click **Users** and select **New user**.</span></span> <span data-ttu-id="c0081-124">Définir le **nom de connexion** à l’utilisateur créé ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="c0081-124">Set the **Login name** to the user created above.</span></span> <span data-ttu-id="c0081-125">Ajoutez l'utilisateur à l'appartenance au rôle de base de données System.Activities.DurableInstancing.InstanceStoreUsers (et autres).</span><span class="sxs-lookup"><span data-stu-id="c0081-125">Add the user to the Database role membership System.Activities.DurableInstancing.InstanceStoreUsers (and others).</span></span> <span data-ttu-id="c0081-126">Notez qu'il est possible que l'utilisateur existe déjà (par exemple, l'utilisateur dbo).</span><span class="sxs-lookup"><span data-stu-id="c0081-126">Note that the user might exist already (for example, user dbo).</span></span>  
  
2.  <span data-ttu-id="c0081-127">Ouvrez le fichier solution PropertyPromotionActivity.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0081-127">Open the PropertyPromotionActivity.sln solution file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="c0081-128">Si vous avez créé le magasin d'instances dans une base de données autre que celle d'une installation locale de SQL Server Express, mettez à jour la chaîne de connexion à la base de données.</span><span class="sxs-lookup"><span data-stu-id="c0081-128">If you created the instance store in a database other than a local installation of SQL Server Express, then you must update the database connection string.</span></span> <span data-ttu-id="c0081-129">Modifiez le fichier App.config sous le **CounterServiceApplication** en définissant la valeur de la `connectionString` de l’attribut le `sqlWorkflowInstanceStorePromotion` nœud afin qu’il pointe vers la base de données de persistance qui a été initialisé dans l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="c0081-129">Alter the App.config file under the **CounterServiceApplication** by setting the value of the `connectionString` attribute on the `sqlWorkflowInstanceStorePromotion` node so that it points to the persistence database that was initialized in step 1.</span></span>  
  
4.  <span data-ttu-id="c0081-130">Générez et exécutez la solution.</span><span class="sxs-lookup"><span data-stu-id="c0081-130">Build and run the solution.</span></span> <span data-ttu-id="c0081-131">Le service WF Compteur et une instance du workflow démarrent ainsi automatiquement.</span><span class="sxs-lookup"><span data-stu-id="c0081-131">This will start the Counter WF service and automatically start a workflow instance.</span></span>  
  
5.  <span data-ttu-id="c0081-132">Sélectionnez rapidement toutes les lignes dans la vue [dbo].[CounterService] de votre base de données de persistance (cette vue a été ajoutée en exécutant CreateInstanceStore.cmd à l'étape 1).</span><span class="sxs-lookup"><span data-stu-id="c0081-132">Quickly select all the rows in the [dbo].[CounterService] view in your persistence database (this view was added by running CreateInstanceStore.cmd in step 1).</span></span> <span data-ttu-id="c0081-133">Un ensemble de résultats semblable au suivant s'affiche :</span><span class="sxs-lookup"><span data-stu-id="c0081-133">You will see a result set similar to the following:</span></span>  
  
    |<span data-ttu-id="c0081-134">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c0081-134">InstanceId</span></span>|<span data-ttu-id="c0081-135">CounterValue</span><span class="sxs-lookup"><span data-stu-id="c0081-135">CounterValue</span></span>|<span data-ttu-id="c0081-136">CounterValueLastUpdated</span><span class="sxs-lookup"><span data-stu-id="c0081-136">CounterValueLastUpdated</span></span>|  
    |----------------|------------------|-----------------------------|  
    |<span data-ttu-id="c0081-137">2FA2C302-929E-4C0D-8C25-768A3DA20CE5</span><span class="sxs-lookup"><span data-stu-id="c0081-137">2FA2C302-929E-4C0D-8C25-768A3DA20CE5</span></span>|<span data-ttu-id="c0081-138">12</span><span class="sxs-lookup"><span data-stu-id="c0081-138">12</span></span>|<span data-ttu-id="c0081-139">2010-02-18 22:48:01.740</span><span class="sxs-lookup"><span data-stu-id="c0081-139">2010-02-18 22:48:01.740</span></span>|  
  
     <span data-ttu-id="c0081-140">À mesure que vous actualisez la vue, vous noterez que CounterValue et CounterValueLastUpdated changent toutes les deux secondes.</span><span class="sxs-lookup"><span data-stu-id="c0081-140">As you keep refreshing the view, you will notice that CounterValue and CounterValueLastUpdated change every two seconds.</span></span> <span data-ttu-id="c0081-141">Il s'agit de l'intervalle auquel le compteur se met à jour.</span><span class="sxs-lookup"><span data-stu-id="c0081-141">This is the interval at which the counter updates itself.</span></span> <span data-ttu-id="c0081-142">CounterValue et CounterValueLastUpdated représentent les propriétés promues de ce workflow.</span><span class="sxs-lookup"><span data-stu-id="c0081-142">CounterValue and CounterValueLastUpdated represent promoted properties for this workflow.</span></span>  
  
## <a name="to-remove-the-sample"></a><span data-ttu-id="c0081-143">Pour supprimer l'exemple</span><span class="sxs-lookup"><span data-stu-id="c0081-143">To remove the sample</span></span>  
  
-   <span data-ttu-id="c0081-144">Exécutez RemoveInstanceStore.cmd dans le répertoire de l'exemple (\WF\Basic\Persistence\PropertyPromotionActivity).</span><span class="sxs-lookup"><span data-stu-id="c0081-144">Run RemoveInstanceStore.cmd in the sample directory (\WF\Basic\Persistence\PropertyPromotionActivity).</span></span>  
  
## <a name="understanding-this-sample"></a><span data-ttu-id="c0081-145">Présentation de l'exemple</span><span class="sxs-lookup"><span data-stu-id="c0081-145">Understanding This Sample</span></span>  
 <span data-ttu-id="c0081-146">Cet exemple contient deux projets et un fichier SQL :</span><span class="sxs-lookup"><span data-stu-id="c0081-146">The sample contains two projects and an SQL file:</span></span>  
  
-   <span data-ttu-id="c0081-147">**CounterServiceApplication** est une application console qui héberge un service WF compteur simple.</span><span class="sxs-lookup"><span data-stu-id="c0081-147">**CounterServiceApplication** is a console application that hosts a simple Counter WF service.</span></span> <span data-ttu-id="c0081-148">Lors de la réception d'un message unidirectionnel par le biais du point de terminaison `Start`, le workflow compte de 0 à 29, incrémentant une variable de compteur toutes les deux secondes.</span><span class="sxs-lookup"><span data-stu-id="c0081-148">Upon receiving a one-way message through the `Start` endpoint, the workflow counts from 0 to 29, incrementing a counter variable every two seconds.</span></span> <span data-ttu-id="c0081-149">Après chaque incrément du compteur, le workflow est persistant et les propriétés promues sont mises à jour dans la vue [dbo].[CounterService].</span><span class="sxs-lookup"><span data-stu-id="c0081-149">After every counter increment, the workflow persists, and the promoted properties are updated in the [dbo].[CounterService] view.</span></span> <span data-ttu-id="c0081-150">Si l'application console s'exécute, elle héberge le service WF et envoie un message au point de terminaison `Start`, ce qui crée une instance WF Compteur.</span><span class="sxs-lookup"><span data-stu-id="c0081-150">When the console application is run, it hosts the WF service and sends a message to the `Start` endpoint, creating a Counter WF instance.</span></span>  
  
-   <span data-ttu-id="c0081-151">**PropertyPromotionActivity** est une bibliothèque de classes qui contient les éléments de configuration, activités de workflow et extensions de workflow qui les **CounterServiceApplication** utilise.</span><span class="sxs-lookup"><span data-stu-id="c0081-151">**PropertyPromotionActivity** is a class library that contains the configuration elements, workflow activities, and workflow extensions that the **CounterServiceApplication** uses.</span></span>  
  
-   <span data-ttu-id="c0081-152">**PropertyPromotionActivitySQLSample.sql** crée et ajoute la vue [dbo]. [ CounterService] à la base de données.</span><span class="sxs-lookup"><span data-stu-id="c0081-152">**PropertyPromotionActivitySQLSample.sql** creates and adds the view [dbo].[CounterService] to the database.</span></span>  
  
### <a name="counterserviceapplication"></a><span data-ttu-id="c0081-153">CounterServiceApplication</span><span class="sxs-lookup"><span data-stu-id="c0081-153">CounterServiceApplication</span></span>  
  
#### <a name="using-the-sqlworkflowinstancestorepromotion-configuration-element"></a><span data-ttu-id="c0081-154">Utilisation de l'élément de configuration SqlWorkflowInstanceStorePromotion</span><span class="sxs-lookup"><span data-stu-id="c0081-154">Using the SqlWorkflowInstanceStorePromotion Configuration Element</span></span>  
 <span data-ttu-id="c0081-155">L'élément de configuration `SqlWorkflowInstanceStorePromotion` hérite de l'élément de configuration `SqlWorkflowInstanceStore`, mais ajoute un élément de configuration supplémentaire nommé `promotionSets`.</span><span class="sxs-lookup"><span data-stu-id="c0081-155">The `SqlWorkflowInstanceStorePromotion` configuration element inherits from the `SqlWorkflowInstanceStore` configuration element, but adds an additional configuration element called `promotionSets`.</span></span> <span data-ttu-id="c0081-156">L'élément `promotionSets` permet de spécifier les propriétés promues via la configuration.</span><span class="sxs-lookup"><span data-stu-id="c0081-156">The `promotionSets` element enables the user to specify promoted properties through configuration.</span></span> <span data-ttu-id="c0081-157">Il s'agit du fichier de configuration utilisé par l'exemple :</span><span class="sxs-lookup"><span data-stu-id="c0081-157">This is the configuration file that is used by the sample:</span></span>  
  
```xml  
<sqlWorkflowInstanceStorePromotion connectionString ="Data Source=.;Initial Catalog=SqlWorkflowInstanceStoreTest;Integrated Security=True;">  
  <promotionSets>  
    <promotionSet name="CounterService">  
      <promotedValue propertyName="Count"/>  
      <promotedValue propertyName="LastIncrementedAt"/>  
    </promotionSet>  
  </promotionSets>  
</sqlWorkflowInstanceStorePromotion>  
```  
  
 <span data-ttu-id="c0081-158">Examinez la définition de la vue [dbo].[CounterService].</span><span class="sxs-lookup"><span data-stu-id="c0081-158">Examine the definition for the [dbo].[CounterService] view.</span></span>  
  
```sql  
create view [dbo].[CounterService] as  
      select [InstanceId],  
 [Value1] as [CounterValue],  
 [Value2] as [CounterValueLastUpdated]  
      from [System.Activities.DurableInstancing].[InstancePromotedProperties]  
      where [PromotionName] = 'CounterService'  
go  
```  
  
 <span data-ttu-id="c0081-159">Si une instance de workflow est persistante, une ligne est insérée dans la vue `InstancePromotedProperties` pour chaque `PromotionSet` defini dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="c0081-159">When a workflow instance persists, a row is inserted into the `InstancePromotedProperties` view for each `PromotionSet` defined in the configuration.</span></span> <span data-ttu-id="c0081-160">Cette ligne contient toutes les propriétés promues de `PromotionSet` (une propriété promue par colonne).</span><span class="sxs-lookup"><span data-stu-id="c0081-160">This row contains all the promoted properties of the `PromotionSet` (one promoted property per column).</span></span> <span data-ttu-id="c0081-161">Ce `PromotionSet` est indexé par le tuple : `InstanceId, PromotionName`.</span><span class="sxs-lookup"><span data-stu-id="c0081-161">This `PromotionSet` is keyed by the tuple: `InstanceId, PromotionName`.</span></span> <span data-ttu-id="c0081-162">Dans cet exemple, un `PromotionSet` est défini dans la configuration dont l'attribut name est `CounterService`.</span><span class="sxs-lookup"><span data-stu-id="c0081-162">In this sample, we have one `PromotionSet` defined in configuration whose name attribute is `CounterService`.</span></span> <span data-ttu-id="c0081-163">Notez que la colonne de valeur `PromotionName` correspond à l'attribut name de l'élément `PromotionSet`.</span><span class="sxs-lookup"><span data-stu-id="c0081-163">Note how the `PromotionName` column value is equal to the name attribute of the `PromotionSet` element.</span></span>  
  
 <span data-ttu-id="c0081-164">L'ordre des éléments `promotedValue` correspond à la position des propriétés promues dans la vue `InstancePromotedProperties`.</span><span class="sxs-lookup"><span data-stu-id="c0081-164">The order of the `promotedValue` elements correlates with the placement of the promoted properties in the `InstancePromotedProperties` view.</span></span> <span data-ttu-id="c0081-165">`Count` est le premier élément `promotedValue`.</span><span class="sxs-lookup"><span data-stu-id="c0081-165">`Count` is the first `promotedValue` element.</span></span> <span data-ttu-id="c0081-166">Par conséquent, il est mappé à la colonne `Value1` dans la vue `InstancePromotedProperties`.</span><span class="sxs-lookup"><span data-stu-id="c0081-166">As a result, it is mapped to the `Value1` column in the `InstancePromotedProperties` view.</span></span> <span data-ttu-id="c0081-167">`LastIncrementedAt` est le deuxième élément `promotedValue`.</span><span class="sxs-lookup"><span data-stu-id="c0081-167">`LastIncrementedAt` is the second `promotedValue` element.</span></span> <span data-ttu-id="c0081-168">Par conséquent, il est mappé à la colonne `Value2` dans la vue `InstancePromotedProperties`.</span><span class="sxs-lookup"><span data-stu-id="c0081-168">As a result, it is mapped to the `Value2` column in the `InstancePromotedProperties` view.</span></span>  
  
#### <a name="using-the-promotevalue-activity"></a><span data-ttu-id="c0081-169">Utilisation de l'activité PromoteValue</span><span class="sxs-lookup"><span data-stu-id="c0081-169">Using the PromoteValue Activity</span></span>  
 <span data-ttu-id="c0081-170">Examinez le fichier CounterService.xamlx dans le Concepteur [!INCLUDE[wf2](../../../../includes/wf2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0081-170">Examine the CounterService.xamlx file in the [!INCLUDE[wf2](../../../../includes/wf2-md.md)] Designer.</span></span> <span data-ttu-id="c0081-171">Notez qu'il existe deux activités spécifiques dans la définition WF : `PromoteValue<DateTime>` et `PromoteValue<Int32>`.</span><span class="sxs-lookup"><span data-stu-id="c0081-171">Notice that there are two special activities in the WF definition: `PromoteValue<DateTime>` and `PromoteValue<Int32>`.</span></span>  
  
 <span data-ttu-id="c0081-172">L'activité `PromoteValue<Int32>` a son membre `Name` défini comme `Count`.</span><span class="sxs-lookup"><span data-stu-id="c0081-172">The `PromoteValue<Int32>` activity has its `Name` member defined as `Count`.</span></span> <span data-ttu-id="c0081-173">Cela correspond au premier élément `promotedValue` dans la configuration, et son membre `Value` est défini comme variable de workflow `Counter`.</span><span class="sxs-lookup"><span data-stu-id="c0081-173">This matches with the first `promotedValue` element in the configuration, and has its `Value` defined as the `Counter` workflow variable.</span></span> <span data-ttu-id="c0081-174">Si le workflow est persistant, la variable de workflow `Counter` est persistante en tant que propriété promue dans la colonne `Value1` de la vue `InstancePromotedProperties`.</span><span class="sxs-lookup"><span data-stu-id="c0081-174">When the workflow persists, the `Counter` workflow variable is persisted as a promoted property into the `Value1` column of the `InstancePromotedProperties` view.</span></span>  
  
 <span data-ttu-id="c0081-175">L'activité `PromoteValue<DateTime>` a son membre `Name` défini comme `LastIncrementedAt`.</span><span class="sxs-lookup"><span data-stu-id="c0081-175">The `PromoteValue<DateTime>` activity has its `Name` member defined as `LastIncrementedAt`.</span></span> <span data-ttu-id="c0081-176">Cela correspond au deuxième élément `promotedValue` dans la configuration, et son membre `Value` est défini comme variable de workflow `TimeLastIncremented`.</span><span class="sxs-lookup"><span data-stu-id="c0081-176">This matches with the second `promotedValue` element in the configuration, and has its `Value` defined as the `TimeLastIncremented` workflow variable.</span></span> <span data-ttu-id="c0081-177">En d'autres termes, si le workflow est persistant, la valeur pour la variable de workflow `TimeLastIncremented` est persistante en tant que propriété promue dans la colonne `Value2` de la vue `InstancePromotedProperties`.</span><span class="sxs-lookup"><span data-stu-id="c0081-177">This means that when the workflow persists, the value for the `TimeLastIncremented` workflow variable will be persisted as a promoted property into the `Value2` column of the `InstancePromotedProperties` view.</span></span>  
  
 <span data-ttu-id="c0081-178">Notez que l'activité `PromotedValue` contient aussi un membre Boolean nommé `ClearExistingPromotedData`.</span><span class="sxs-lookup"><span data-stu-id="c0081-178">Note that the `PromotedValue` activity also has a Boolean member called `ClearExistingPromotedData`.</span></span> <span data-ttu-id="c0081-179">Si la valeur `true` est affectée à ce membre, toutes les valeurs de propriété promue sont supprimées jusqu'à ce point dans le workflow.</span><span class="sxs-lookup"><span data-stu-id="c0081-179">When this member is set to `true`, this clears all the promoted property values up to that point in the workflow.</span></span> <span data-ttu-id="c0081-180">Par exemple, si une activité Sequence est définie comme suit :</span><span class="sxs-lookup"><span data-stu-id="c0081-180">For example, if a Sequence activity is defined as follows:</span></span>  
  
1.  <span data-ttu-id="c0081-181">PromoteValue {nom = « Count », valeur = 3}</span><span class="sxs-lookup"><span data-stu-id="c0081-181">PromoteValue { Name = "Count", Value = 3}</span></span>  
  
2.  <span data-ttu-id="c0081-182">PromoteValue {nom = « LastIncrementedAt », valeur = 1-1-2000}</span><span class="sxs-lookup"><span data-stu-id="c0081-182">PromoteValue {Name = "LastIncrementedAt", Value = 1-1-2000 }</span></span>  
  
3.  <span data-ttu-id="c0081-183">Persister</span><span class="sxs-lookup"><span data-stu-id="c0081-183">Persist</span></span>  
  
4.  <span data-ttu-id="c0081-184">PromoteValue {nom = « Count », valeur = 4, ClearExistingPromotedData = true}</span><span class="sxs-lookup"><span data-stu-id="c0081-184">PromoteValue {Name = "Count", Value = 4, ClearExistingPromotedData = true}</span></span>  
  
5.  <span data-ttu-id="c0081-185">Persister</span><span class="sxs-lookup"><span data-stu-id="c0081-185">Persist</span></span>  
  
 <span data-ttu-id="c0081-186">Sur la deuxième persistance, la valeur promue pour `Count` sera 4.</span><span class="sxs-lookup"><span data-stu-id="c0081-186">On the second persist, the promoted value for `Count` will be 4.</span></span> <span data-ttu-id="c0081-187">Toutefois, la valeur promue pour `LastIncrementedAt` sera `NULL`.</span><span class="sxs-lookup"><span data-stu-id="c0081-187">However, the promoted value for `LastIncrementedAt` will be `NULL`.</span></span> <span data-ttu-id="c0081-188">Si la valeur `ClearExistingPromotedData` n'a pas été affectée à `true` à l'étape 4, après la deuxième persistance, la valeur promue pour Count sera 4.</span><span class="sxs-lookup"><span data-stu-id="c0081-188">If `ClearExistingPromotedData` was not set to `true` for step 4, then after the second persist, the promoted value for Count would be 4.</span></span> <span data-ttu-id="c0081-189">Par conséquent, la valeur promue pour `LastIncrementedAt` sera toujours 1-1-2000.</span><span class="sxs-lookup"><span data-stu-id="c0081-189">As a result, the promoted value for `LastIncrementedAt` would still be 1-1-2000.</span></span>  
  
### <a name="propertypromotionactivity"></a><span data-ttu-id="c0081-190">PropertyPromotionActivity</span><span class="sxs-lookup"><span data-stu-id="c0081-190">PropertyPromotionActivity</span></span>  
 <span data-ttu-id="c0081-191">Cette bibliothèque de classes contient les classes publiques suivantes pour simplifier l'utilisation de la fonctionnalité Promotion de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>.</span><span class="sxs-lookup"><span data-stu-id="c0081-191">This class library contains the following public classes to simplify use of the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Promotion feature.</span></span>  
  
#### <a name="promotevalue-class"></a><span data-ttu-id="c0081-192">Classe PromoteValue</span><span class="sxs-lookup"><span data-stu-id="c0081-192">PromoteValue Class</span></span>  
 <span data-ttu-id="c0081-193">Cette classe promeut une seule propriété.</span><span class="sxs-lookup"><span data-stu-id="c0081-193">This class promotes one property.</span></span> <span data-ttu-id="c0081-194">Le nom de la propriété promue doit correspondre à l'attribut name d'un élément `promotedValue` dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="c0081-194">The name of the promoted property should match a name attribute of a `promotedValue` element in the configuration.</span></span> <span data-ttu-id="c0081-195">Cette activité peut être utilisée dans le Concepteur de Workflow.</span><span class="sxs-lookup"><span data-stu-id="c0081-195">This activity can be used in the Workflow Designer.</span></span> <span data-ttu-id="c0081-196">Pour obtenir un exemple d'utilisation, consultez CounterServiceApplication.</span><span class="sxs-lookup"><span data-stu-id="c0081-196">See the CounterServiceApplication for an example usage.</span></span>  
  
```csharp  
public class PromoteValue<T> : CodeActivity  
{  
    public PromoteValue()  
    {  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public string Name { get; set; }  
    public InArgument<T> Value { get; set; }  
}  
```  
  
 <span data-ttu-id="c0081-197">ClearExistingPromotedData (Bool)</span><span class="sxs-lookup"><span data-stu-id="c0081-197">ClearExistingPromotedData (Bool)</span></span>  
 <span data-ttu-id="c0081-198">Supprime toutes les valeurs qui ont été promues avant cette activité.</span><span class="sxs-lookup"><span data-stu-id="c0081-198">Clears all values that were promoted before this activity.</span></span>  
  
 <span data-ttu-id="c0081-199">Name (string)</span><span class="sxs-lookup"><span data-stu-id="c0081-199">Name (string)</span></span>  
 <span data-ttu-id="c0081-200">Nom représentant cette propriété.</span><span class="sxs-lookup"><span data-stu-id="c0081-200">The name that represents this property.</span></span> <span data-ttu-id="c0081-201">Il doit correspondre à l’attribut de nom d’un \<promotedValue > élément dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="c0081-201">This should match the name attribute of a \<promotedValue> element in the configuration.</span></span>  
  
 <span data-ttu-id="c0081-202">Valeur (InArgument\<T >)</span><span class="sxs-lookup"><span data-stu-id="c0081-202">Value (InArgument\<T>)</span></span>  
 <span data-ttu-id="c0081-203">Variable/valeur à stocker dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="c0081-203">The variable / value that you want to store in the column.</span></span>  
  
#### <a name="promotevalues-class"></a><span data-ttu-id="c0081-204">Classe PromoteValues</span><span class="sxs-lookup"><span data-stu-id="c0081-204">PromoteValues Class</span></span>  
 <span data-ttu-id="c0081-205">Promeut plusieurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="c0081-205">Promotes multiple properties.</span></span> <span data-ttu-id="c0081-206">Les noms des propriétés promues doivent correspondre à tous les attributs name des éléments `promotedValue` dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="c0081-206">The names of the promoted properties should match all name attributes in the `promotedValue` elements in the configuration.</span></span> <span data-ttu-id="c0081-207">L'utilisation est similaire à celle de l'activité `PromoteValue`, excepté que plusieurs propriétés peuvent être promues simultanément.</span><span class="sxs-lookup"><span data-stu-id="c0081-207">Usage is similar to the `PromoteValue` activity, except for the fact that multiple properties can be promoted at the same time.</span></span> <span data-ttu-id="c0081-208">Cette activité ne peut pas être utilisée dans le Concepteur de Workflow.</span><span class="sxs-lookup"><span data-stu-id="c0081-208">This activity cannot be used in the Workflow Designer.</span></span>  
  
```  
public class PromoteValues : CodeActivity  
{  
    public PromoteValues()  
    {  
        this.ValuesToPromote = new Dictionary<string, InArgument>();  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public IDictionary<string, InArgument> ValuesToPromote { get; set; }  
}  
```  
  
#### <a name="sqlworkflowinstancestorepromotionbehavior"></a><span data-ttu-id="c0081-209">SqlWorkflowInstanceStorePromotionBehavior</span><span class="sxs-lookup"><span data-stu-id="c0081-209">SqlWorkflowInstanceStorePromotionBehavior</span></span>  
 <span data-ttu-id="c0081-210">Dérive de `SqlWorkflowInstanceStoreBehavior`.</span><span class="sxs-lookup"><span data-stu-id="c0081-210">Derives from `SqlWorkflowInstanceStoreBehavior`.</span></span> <span data-ttu-id="c0081-211">Cette classe dérivée ajoute un participant de persistance personnalisé (qui fait également partie de cette bibliothèque) en tant qu'extension de workflow.</span><span class="sxs-lookup"><span data-stu-id="c0081-211">This derived class adds a custom persistence participant (also a part of this library) as a workflow extension.</span></span> <span data-ttu-id="c0081-212">L'implémentation des deux activités de workflow précédentes repose sur ce participant de persistance personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c0081-212">The implementation of the previous two workflow activities relies on this custom persistence participant.</span></span>  
  
```  
public class SqlWorkflowInstanceStorePromotionBehavior :  
             SqlWorkflowInstanceStoreBehavior, IServiceBehavior  
{  
        public void Promote(string name, IEnumerable<string> promoteAsSqlVariant,  
                            IEnumerable<string> promoteAsBinary)  
  
}  
```  
  
 <span data-ttu-id="c0081-213">Cette bibliothèque de classes contient l'implémentation de `ConfigurationElement` pour le `SqlWorkflowInstanceStorePromotionElement` et un participant de persistance personnalisé utilisé par les activités de promotion précédentes.</span><span class="sxs-lookup"><span data-stu-id="c0081-213">This class library also contains the `ConfigurationElement` implementation for the `SqlWorkflowInstanceStorePromotionElement` and a custom persistence participant used by the previous promotion activities.</span></span>  
  
### <a name="propertypromotionactivitysqlsample"></a><span data-ttu-id="c0081-214">PropertyPromotionActivitySQLSample</span><span class="sxs-lookup"><span data-stu-id="c0081-214">PropertyPromotionActivitySQLSample</span></span>  
 <span data-ttu-id="c0081-215">Ce fichier SQL crée une vue `[dbo].[CounterService]` en plus de la vue `[InstancePromotedProperties]` pour interroger toutes les instances qui ont un CounterService Promotion défini.</span><span class="sxs-lookup"><span data-stu-id="c0081-215">This SQL file creates a `[dbo].[CounterService]` view in addition to the `[InstancePromotedProperties]` view for querying all instances that have a CounterService Promotion set.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c0081-216">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c0081-216">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c0081-217">Recherchez le répertoire (par défaut) suivant avant de continuer :</span><span class="sxs-lookup"><span data-stu-id="c0081-217">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c0081-218">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c0081-218">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c0081-219">Cet exemple se trouve dans le répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="c0081-219">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\PropertyPromotionActivity`  
  
## <a name="see-also"></a><span data-ttu-id="c0081-220">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0081-220">See Also</span></span>  
 [<span data-ttu-id="c0081-221">Hébergement de AppFabric et exemples de persistance</span><span class="sxs-lookup"><span data-stu-id="c0081-221">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
