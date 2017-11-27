---
title: '&lt;etwTracking&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 583c5bcb1e864b79f80a9c3095ed8ce7b74a19eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltetwtrackinggt"></a><span data-ttu-id="35565-102">&lt;etwTracking&gt;</span><span class="sxs-lookup"><span data-stu-id="35565-102">&lt;etwTracking&gt;</span></span>
<span data-ttu-id="35565-103">Comportement de service qui permet à un service à utiliser à l’aide du suivi ETW un <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="35565-103">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="35565-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="35565-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="35565-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="35565-105">\<behaviors></span></span>  
<span data-ttu-id="35565-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="35565-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="35565-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="35565-107">\<behavior></span></span>  
<span data-ttu-id="35565-108">\<etwTracking ></span><span class="sxs-lookup"><span data-stu-id="35565-108">\<etwTracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35565-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35565-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35565-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="35565-110">Attributes and Elements</span></span>  
 <span data-ttu-id="35565-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="35565-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35565-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="35565-112">Attributes</span></span>  
  
|<span data-ttu-id="35565-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="35565-113">Attribute</span></span>|<span data-ttu-id="35565-114">Description</span><span class="sxs-lookup"><span data-stu-id="35565-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="35565-115">profileName</span><span class="sxs-lookup"><span data-stu-id="35565-115">profileName</span></span>|<span data-ttu-id="35565-116">Chaîne qui spécifie le nom du modèle de suivi a associé à ce comportement.</span><span class="sxs-lookup"><span data-stu-id="35565-116">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35565-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="35565-117">Child Elements</span></span>  
 <span data-ttu-id="35565-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="35565-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35565-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="35565-119">Parent Elements</span></span>  
  
|<span data-ttu-id="35565-120">Élément</span><span class="sxs-lookup"><span data-stu-id="35565-120">Element</span></span>|<span data-ttu-id="35565-121">Description</span><span class="sxs-lookup"><span data-stu-id="35565-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35565-122">\<comportement > de \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="35565-122">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="35565-123">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="35565-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35565-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="35565-124">Remarks</span></span>  
 <span data-ttu-id="35565-125">Lorsqu'il est ajouté à la configuration de comportement du service, cet élément de configuration configure un participant au suivi sur un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="35565-125">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="35565-126">Les participants au suivi permettent d'obtenir les données de suivi émises du flux de travail et de les stocker dans différents médias.</span><span class="sxs-lookup"><span data-stu-id="35565-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="35565-127">De la même manière, tout post-traitement effectué sur les enregistrements de suivi peut également être réalisé dans le participant au suivi.</span><span class="sxs-lookup"><span data-stu-id="35565-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35565-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="35565-128">Example</span></span>  
 <span data-ttu-id="35565-129">L'exemple suivant présente la configuration du participant au suivi ETW standard dans le fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="35565-129">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="35565-130">L’Id de fournisseur par le Participant de suivi ETW pour écrire les enregistrements de suivi ETW est défini dans le  **\<diagnostics >** section.</span><span class="sxs-lookup"><span data-stu-id="35565-130">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="35565-131">Un profil est associé au participant au suivi pour spécifier les enregistrements de suivi auxquels il est abonné.</span><span class="sxs-lookup"><span data-stu-id="35565-131">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="35565-132">Cela est défini par le **profileName** attribut de la  **\<Ajouter >** élément.</span><span class="sxs-lookup"><span data-stu-id="35565-132">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="35565-133">Une fois qu’ils sont définis, le participant au suivi est ajouté à la  **\<etwTracking >** comportement de service.</span><span class="sxs-lookup"><span data-stu-id="35565-133">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="35565-134">Les participants au suivi sélectionnés sont ajoutés aux extensions de l’instance de flux de travail, afin qu’ils commencent à recevoir les enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="35565-134">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="35565-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35565-135">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>  
 [<span data-ttu-id="35565-136">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="35565-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="35565-137">Participants de suivi</span><span class="sxs-lookup"><span data-stu-id="35565-137">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
