---
title: '&lt;participants&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 560dd0bb-f9fb-423c-8857-2101a3654b06
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a6e00ccbe4a43fd1dbf96a40d5bc4bca70ea7f78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltparticipantsgt"></a><span data-ttu-id="d3d8e-102">&lt;participants&gt;</span><span class="sxs-lookup"><span data-stu-id="d3d8e-102">&lt;participants&gt;</span></span>
<span data-ttu-id="d3d8e-103">Configurez une liste de participants au suivi qui écoutent les enregistrements de suivi émis directement du runtime et les traitent en fonction de leur configuration.</span><span class="sxs-lookup"><span data-stu-id="d3d8e-103">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="d3d8e-104">Cela inclut l'écriture dans une sortie spécifique (par exemple, un fichier, une console ou le suivi d'événements pour Windows [ETW]), le traitement/regroupement des enregistrements ou toute autre combinaison requise.</span><span class="sxs-lookup"><span data-stu-id="d3d8e-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="d3d8e-105">Pour plus d’informations de suivi de flux de travail et les participants de suivi, consultez [suivi et traçage de Workflow](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) et [les participants au suivi](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="d3d8e-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="d3d8e-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="d3d8e-106">\<system.serviceModel></span></span>  
<span data-ttu-id="d3d8e-107">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="d3d8e-107">\<tracking></span></span>  
<span data-ttu-id="d3d8e-108">\<participants ></span><span class="sxs-lookup"><span data-stu-id="d3d8e-108">\<participants></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3d8e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3d8e-109">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" 
         profileName="String" 
         type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3d8e-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d3d8e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d3d8e-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d3d8e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3d8e-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="d3d8e-112">Attributes</span></span>  
 <span data-ttu-id="d3d8e-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d3d8e-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d3d8e-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d3d8e-114">Child Elements</span></span>  
  
|<span data-ttu-id="d3d8e-115">Élément</span><span class="sxs-lookup"><span data-stu-id="d3d8e-115">Element</span></span>|<span data-ttu-id="d3d8e-116">Description</span><span class="sxs-lookup"><span data-stu-id="d3d8e-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3d8e-117">\<add></span><span class="sxs-lookup"><span data-stu-id="d3d8e-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="d3d8e-118">Contient les paramètres d'un participant au suivi.</span><span class="sxs-lookup"><span data-stu-id="d3d8e-118">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d3d8e-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d3d8e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d3d8e-120">Élément</span><span class="sxs-lookup"><span data-stu-id="d3d8e-120">Element</span></span>|<span data-ttu-id="d3d8e-121">Description</span><span class="sxs-lookup"><span data-stu-id="d3d8e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3d8e-122">\<suivi ></span><span class="sxs-lookup"><span data-stu-id="d3d8e-122">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="d3d8e-123">Représente une section de configuration permettant de définir les paramètres de suivi d'un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="d3d8e-123">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3d8e-124">Notes</span><span class="sxs-lookup"><span data-stu-id="d3d8e-124">Remarks</span></span>  
 <span data-ttu-id="d3d8e-125">Les participants au suivi permettent d'obtenir les données de suivi émises du flux de travail et de les stocker dans différents médias.</span><span class="sxs-lookup"><span data-stu-id="d3d8e-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="d3d8e-126">De la même manière, tout post-traitement effectué sur les enregistrements de suivi peut également être réalisé dans le participant au suivi.</span><span class="sxs-lookup"><span data-stu-id="d3d8e-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="d3d8e-127">Plusieurs participants au suivi peuvent consommer les événements de suivi simultanément.</span><span class="sxs-lookup"><span data-stu-id="d3d8e-127">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="d3d8e-128">Chaque participant au suivi peut être associé à un modèle de suivi différent.</span><span class="sxs-lookup"><span data-stu-id="d3d8e-128">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="d3d8e-129">Un participant au suivi standard est fourni, il écrit les enregistrements de suivi dans une session ETW.</span><span class="sxs-lookup"><span data-stu-id="d3d8e-129">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="d3d8e-130">Le participant est configuré sur un service de flux de travail en ajoutant un comportement spécifique au suivi dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="d3d8e-130">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="d3d8e-131">L'activation d'un participant au suivi ETW permet d'afficher les enregistrements de suivi dans l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="d3d8e-131">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="d3d8e-132">Si cela ne répond pas à vos besoins, vous pouvez également écrire un participant de suivi personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d3d8e-132">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3d8e-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3d8e-133">Example</span></span>  
 <span data-ttu-id="d3d8e-134">L'exemple suivant présente la configuration du participant au suivi ETW standard dans le fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="d3d8e-134">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="d3d8e-135">L’Id de fournisseur par le Participant de suivi ETW pour écrire les enregistrements de suivi ETW est défini dans le  **\<diagnostics >** section.</span><span class="sxs-lookup"><span data-stu-id="d3d8e-135">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="d3d8e-136">Un profil est associé au participant au suivi pour spécifier les enregistrements de suivi auxquels il est abonné.</span><span class="sxs-lookup"><span data-stu-id="d3d8e-136">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="d3d8e-137">Cela est défini par le **profileName** attribut de la  **\<Ajouter >** élément.</span><span class="sxs-lookup"><span data-stu-id="d3d8e-137">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="d3d8e-138">Une fois qu’ils sont définis, le participant au suivi est ajouté à la  **\<etwTracking >** comportement de service.</span><span class="sxs-lookup"><span data-stu-id="d3d8e-138">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="d3d8e-139">Les participants au suivi sélectionnés sont ajoutés aux extensions de l’instance de flux de travail, afin qu’ils commencent à recevoir les enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="d3d8e-139">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml
<configuration>   
  <system.web>   
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>   
  </system.web>   
  <system.serviceModel>   
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />                
    <tracking>   
      <participants>   
        <add name="EtwTrackingParticipant"   
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"   
             profileName="HealthMonitoring_Tracking_Profile"/>   
      </participants>   
    </tracking>   
    <behaviors>   
      <serviceBehaviors>   
        <behavior>   
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>   
      </serviceBehaviors>   
    </behaviors>   
  </system.serviceModel>   
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3d8e-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3d8e-140">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>  
 [<span data-ttu-id="d3d8e-141">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="d3d8e-141">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="d3d8e-142">Participants de suivi</span><span class="sxs-lookup"><span data-stu-id="d3d8e-142">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
