---
title: Service Auditing Behavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0e7e85ac2aa5be9614946418f0df676ea1cb7dd7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="service-auditing-behavior"></a><span data-ttu-id="7d997-102">Service Auditing Behavior</span><span class="sxs-lookup"><span data-stu-id="7d997-102">Service Auditing Behavior</span></span>
<span data-ttu-id="7d997-103">Cet exemple montre comment utiliser <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> pour activer l'audit des événements de sécurité pendant des opérations de service.</span><span class="sxs-lookup"><span data-stu-id="7d997-103">This sample demonstrates how to use the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to enable auditing of security events during service operations.</span></span> <span data-ttu-id="7d997-104">Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="7d997-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="7d997-105">Le service et le client ont été configurés à l’aide de la [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="7d997-105">The service and client have been configured using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="7d997-106">Le `mode` attribut de la [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) a été défini sur `Message` et `clientCredentialType` a été défini sur `Windows`.</span><span class="sxs-lookup"><span data-stu-id="7d997-106">The `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="7d997-107">Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="7d997-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d997-108">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="7d997-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7d997-109">Le fichier de configuration de service utilise l'élément `serviceSecurityAudit` pour configurer l'audit.</span><span class="sxs-lookup"><span data-stu-id="7d997-109">The service configuration file uses the `serviceSecurityAudit` element to configure auditing.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      ...  
<!-- serviceSecurityAudit allows specification of audit location   
     and whether to audit success, failure or both. This service   
     logs success and failure of messageAuthentication   
     to the default location -->  
     <serviceSecurityAudit auditLogLocation ="Default" messageAuthenticationAuditLevel = "SuccessOrFailure" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="7d997-110">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="7d997-110">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="7d997-111">Appuyez sur ENTER dans la fenêtre de console pour arrêter le client.</span><span class="sxs-lookup"><span data-stu-id="7d997-111">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="7d997-112">Les journaux d'audit résultants peuvent être consultés en exécutant l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="7d997-112">The resulting audit logs can be seen by running the Event Viewer.</span></span> <span data-ttu-id="7d997-113">Par défaut, les événements d'audit peuvent être consultés sur Windows XP dans le journal d'application, tandis que sur Windows Server 2003 et Windows Vista, ils peuvent être consultés dans le journal de sécurité.</span><span class="sxs-lookup"><span data-stu-id="7d997-113">By default, on Windows XP the audit events can be seen in the Application Log while on Windows Server 2003 and Windows Vista, the audit events can be seen in the Security Log.</span></span> <span data-ttu-id="7d997-114">Les événements d'audit peuvent être consultés sur Windows Server 2008 et Windows 7 dans les journaux d'application et de services.</span><span class="sxs-lookup"><span data-stu-id="7d997-114">On Windows Server 2008 and Windows 7, the audit events can be seen in the Applications and Services logs.</span></span> <span data-ttu-id="7d997-115">L’emplacement des événements d’audit peut être spécifié en définissant le `auditLogLocation` l’attribut « Application » ou « Sécurité ».</span><span class="sxs-lookup"><span data-stu-id="7d997-115">The location of audit events can be specified by setting the `auditLogLocation` attribute to "Application" or "Security".</span></span> <span data-ttu-id="7d997-116">Pour plus d’informations, consultez [Comment : auditer les événements de sécurité](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="7d997-116">For more information, see [How to: Audit Security Events](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).</span></span> <span data-ttu-id="7d997-117">Si les événements sont écrits dans le journal de sécurité, LocalSecurityPolicy-> Enable Object Access doit avoir la valeur « Success » et « Failure ».</span><span class="sxs-lookup"><span data-stu-id="7d997-117">If the events are written in the Security Log the LocalSecurityPolicy-> Enable Object Access should be set for "Success" and "Failure".</span></span>  
  
 <span data-ttu-id="7d997-118">Lors de la consultation du journal des événements, la source des événements d'audit est « ServiceModel Audit 3.0.0.0 ».</span><span class="sxs-lookup"><span data-stu-id="7d997-118">When looking at the event log, the source of the audit events is "ServiceModel Audit 3.0.0.0".</span></span> <span data-ttu-id="7d997-119">Enregistrements d’audit de l’authentification message portent la catégorie « messageauthentication », tandis qu’enregistrements d’audit d’autorisation du service portent la catégorie « ServiceAuthorization ».</span><span class="sxs-lookup"><span data-stu-id="7d997-119">Message authentication audit records have a category of "MessageAuthentication" while service authorization audit records have a category of "ServiceAuthorization".</span></span>  
  
 <span data-ttu-id="7d997-120">Les événements de l'audit d'authentification du message permettent de savoir si le message a été falsifié, s'il a expiré et si le client peut s'authentifier auprès du service.</span><span class="sxs-lookup"><span data-stu-id="7d997-120">Message authentication audit events cover whether the message was tampered with, whether the message has expired, and whether the client can authenticate to the service.</span></span> <span data-ttu-id="7d997-121">Ils fournissent des informations sur la réussite ou l'échec de l'authentification, l'identité du client, le point de terminaison auquel le message a été envoyé et l'action associée au message.</span><span class="sxs-lookup"><span data-stu-id="7d997-121">They provide information about whether the authentication succeeded or failed along with the identity of the client, and the endpoint the message was sent to along with the action associated with the message.</span></span>  
  
 <span data-ttu-id="7d997-122">Les événements de l'audit d'autorisation du service permettent de connaître la décision d'autorisation prise par un gestionnaire d'autorisation du service.</span><span class="sxs-lookup"><span data-stu-id="7d997-122">Service authorization audit events cover the authorization decision made by a service authorization manager.</span></span> <span data-ttu-id="7d997-123">Ils fournissent des informations sur la réussite ou l'échec de l'autorisation, ainsi que l'identité du client, le point de terminaison auquel le message a été envoyé, l'action associée au message, l'identificateur du contexte d'autorisation généré à partir du message entrant et le type du gestionnaire d'autorisations qui a pris la décision d'accès.</span><span class="sxs-lookup"><span data-stu-id="7d997-123">They provide information about whether authorization succeeded or failed along with the identity of the client, the endpoint the message was sent to, the action associated with the message, the identifier of the authorization context that was generated from the incoming message, and the type of the authorization manager that made the access decision.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7d997-124">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="7d997-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7d997-125">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7d997-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="7d997-126">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7d997-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="7d997-127">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7d997-127">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d997-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d997-128">See Also</span></span>  
 [<span data-ttu-id="7d997-129">L’audit</span><span class="sxs-lookup"><span data-stu-id="7d997-129">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [<span data-ttu-id="7d997-130">Comment : auditer les événements de sécurité</span><span class="sxs-lookup"><span data-stu-id="7d997-130">How to: Audit Security Events</span></span>](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
