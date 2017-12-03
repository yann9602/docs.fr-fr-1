---
title: "&lt;serviceAuthorization&gt;, élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bc04552b9b2ecd85a520ed16ae9a6ee0dfc98a46
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltserviceauthorizationgt-element"></a><span data-ttu-id="dd37a-102">&lt;serviceAuthorization&gt;, élément</span><span class="sxs-lookup"><span data-stu-id="dd37a-102">&lt;serviceAuthorization&gt; element</span></span>
<span data-ttu-id="dd37a-103">Spécifie les paramètres qui autorisent l'accès pour l'entretien des opérations</span><span class="sxs-lookup"><span data-stu-id="dd37a-103">Specifies settings that authorize access to service operations</span></span>  
  
 <span data-ttu-id="dd37a-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="dd37a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dd37a-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="dd37a-105">\<behaviors></span></span>  
<span data-ttu-id="dd37a-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="dd37a-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="dd37a-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="dd37a-107">\<behavior></span></span>  
<span data-ttu-id="dd37a-108">\<serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="dd37a-108">\<serviceAuthorization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd37a-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd37a-109">Syntax</span></span>  
  
```xml  
<serviceAuthorization  
     impersonateCallerForAllOperations="Boolean"  
      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"  
      roleProviderName="String"  
      serviceAuthorizationManagerType="String" />  
      <authorizationPolicies>  
         <add policyType="String" />  
      </authorizationPolicies>  
</serviceAuthorization>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd37a-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="dd37a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dd37a-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="dd37a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd37a-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="dd37a-112">Attributes</span></span>  
  
|<span data-ttu-id="dd37a-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="dd37a-113">Attribute</span></span>|<span data-ttu-id="dd37a-114">Description</span><span class="sxs-lookup"><span data-stu-id="dd37a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd37a-115">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="dd37a-115">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="dd37a-116">Valeur booléenne qui spécifie si toutes les opérations du service personnifient l'appelant.</span><span class="sxs-lookup"><span data-stu-id="dd37a-116">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="dd37a-117">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="dd37a-117">The default is `false`.</span></span><br /><br /> <span data-ttu-id="dd37a-118">Lorsqu'une opération de service spécifique personnifie l'appelant, le contexte du thread est basculé sur le contexte de l'appelant avant d'exécuter le service spécifié.</span><span class="sxs-lookup"><span data-stu-id="dd37a-118">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="dd37a-119">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="dd37a-119">principalPermissionMode</span></span>|<span data-ttu-id="dd37a-120">Définit la principal de sécurité utilisée pour effectuer les opérations sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="dd37a-120">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="dd37a-121">Les valeurs sont notamment les suivantes :</span><span class="sxs-lookup"><span data-stu-id="dd37a-121">Values include the following:</span></span><br /><br /> <span data-ttu-id="dd37a-122">-Aucun</span><span class="sxs-lookup"><span data-stu-id="dd37a-122">-   None</span></span><br /><span data-ttu-id="dd37a-123">-UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="dd37a-123">-   UseWindowsGroups</span></span><br /><span data-ttu-id="dd37a-124">-UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="dd37a-124">-   UseAspNetRoles</span></span><br /><span data-ttu-id="dd37a-125">-Custom</span><span class="sxs-lookup"><span data-stu-id="dd37a-125">-   Custom</span></span><br /><br /> <span data-ttu-id="dd37a-126">La valeur par défaut est UseWindowsGroups.</span><span class="sxs-lookup"><span data-stu-id="dd37a-126">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="dd37a-127">La valeur est de type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span><span class="sxs-lookup"><span data-stu-id="dd37a-127">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="dd37a-128">Pour plus d’informations sur l’utilisation de cet attribut, consultez [Comment : restreindre l’accès à la classe PrincipalPermissionAttribute](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span><span class="sxs-lookup"><span data-stu-id="dd37a-128">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="dd37a-129">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="dd37a-129">roleProviderName</span></span>|<span data-ttu-id="dd37a-130">Chaîne qui spécifie le nom du fournisseur de rôles, qui fournit des informations de rôle pour une application de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="dd37a-130">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="dd37a-131">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="dd37a-131">The default is an empty string.</span></span>|  
|<span data-ttu-id="dd37a-132">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="dd37a-132">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="dd37a-133">Chaîne qui contient le type du gestionnaire d'autorisations de service.</span><span class="sxs-lookup"><span data-stu-id="dd37a-133">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="dd37a-134">Pour plus d'informations, consultez <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="dd37a-134">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd37a-135">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dd37a-135">Child Elements</span></span>  
  
|<span data-ttu-id="dd37a-136">Élément</span><span class="sxs-lookup"><span data-stu-id="dd37a-136">Element</span></span>|<span data-ttu-id="dd37a-137">Description</span><span class="sxs-lookup"><span data-stu-id="dd37a-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dd37a-138">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="dd37a-138">authorizationPolicies</span></span>|<span data-ttu-id="dd37a-139">Contient une collection des types de la stratégie d'autorisation, qui peuvent être ajoutés à l'aide du mot clé `add`.</span><span class="sxs-lookup"><span data-stu-id="dd37a-139">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="dd37a-140">Chaque stratégie d'autorisation contient un attribut `policyType` requis unique qui est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="dd37a-140">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="dd37a-141">L'attribut spécifie une stratégie d'autorisation, qui active la transformation d'un jeu de revendications d'entrée dans un autre jeu de revendications.</span><span class="sxs-lookup"><span data-stu-id="dd37a-141">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="dd37a-142">Le contrôle d'accès peut être accordé ou refusé en fonction de cette opération.</span><span class="sxs-lookup"><span data-stu-id="dd37a-142">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="dd37a-143">Pour plus d'informations, consultez <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="dd37a-143">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dd37a-144">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="dd37a-144">Parent Elements</span></span>  
  
|<span data-ttu-id="dd37a-145">Élément</span><span class="sxs-lookup"><span data-stu-id="dd37a-145">Element</span></span>|<span data-ttu-id="dd37a-146">Description</span><span class="sxs-lookup"><span data-stu-id="dd37a-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd37a-147">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="dd37a-147">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="dd37a-148">Contient une collection de paramètres pour le comportement d’un service.</span><span class="sxs-lookup"><span data-stu-id="dd37a-148">Contains a collection of settings for the behavior of a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd37a-149">Remarques</span><span class="sxs-lookup"><span data-stu-id="dd37a-149">Remarks</span></span>  
 <span data-ttu-id="dd37a-150">Cette section contient des éléments qui affectent l'autorisation, les fournisseurs de rôles personnalisés et l'emprunt d'identité.</span><span class="sxs-lookup"><span data-stu-id="dd37a-150">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
 <span data-ttu-id="dd37a-151">L'attribut `principalPermissionMode` spécifie les groupes d'utilisateurs à utiliser lors de l'autorisation d'utilisation d'une méthode protégée.</span><span class="sxs-lookup"><span data-stu-id="dd37a-151">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="dd37a-152">La valeur par défaut (`UseWindowsGroups`) spécifie qu'une identité essayant d'accéder à une ressource est recherchée dans les groupes Windows, comme Administrateurs ou Utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="dd37a-152">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="dd37a-153">Vous pouvez également spécifier `UseAspNetRoles` à utiliser un fournisseur de rôles personnalisé configuré sous la \<system.web > élément, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="dd37a-153">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code.</span></span>  
  
```xml  
<system.web>  
  <membership defaultProvider="SqlProvider"   
   userIsOnlineTimeWindow="15">  
     <providers>  
       <clear />  
       <add   
          name="SqlProvider"   
          type="System.Web.Security.SqlMembershipProvider"   
          connectionStringName="SqlConn"  
          applicationName="MembershipProvider"  
          enablePasswordRetrieval="false"  
          enablePasswordReset="false"  
          requiresQuestionAndAnswer="false"  
          requiresUniqueEmail="true"  
          passwordFormat="Hashed" />  
     </providers>  
   </membership>  
  <!-- Other configuration code not shown.-->  
</system.web>  
```  
  
 <span data-ttu-id="dd37a-154">Le code suivant présente le `roleProviderName` utilisé avec l'attribut `principalPermissionMode`.</span><span class="sxs-lookup"><span data-stu-id="dd37a-154">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute.</span></span>  
  
```xml  
<behaviors>  
   <behavior name="ServiceBehaviour">  
     <serviceAuthorization principalPermissionMode ="UseAspNetRoles"   
                           roleProviderName ="SqlProvider" />  
   </behavior>   
<!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
 <span data-ttu-id="dd37a-155">Pour obtenir un exemple détaillé de l’utilisation de cet élément de configuration, consultez [autorisant l’accès aux opérations de Service](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md) et [stratégie d’autorisation](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="dd37a-155">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd37a-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd37a-156">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 [<span data-ttu-id="dd37a-157">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="dd37a-157">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="dd37a-158">Autoriser l’accès aux opérations de Service</span><span class="sxs-lookup"><span data-stu-id="dd37a-158">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="dd37a-159">Comment : créer un gestionnaire d’autorisation personnalisé pour un Service</span><span class="sxs-lookup"><span data-stu-id="dd37a-159">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="dd37a-160">Guide pratique pour restreindre l’accès avec la classe PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="dd37a-160">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 [<span data-ttu-id="dd37a-161">Stratégie d’autorisation</span><span class="sxs-lookup"><span data-stu-id="dd37a-161">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
