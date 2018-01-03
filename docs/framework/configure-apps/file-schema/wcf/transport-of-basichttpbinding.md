---
title: '&lt;transport&gt; de &lt;basicHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 575bd9491573be949a2a8ea0d0b6a22cb399b977
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="lttransportgt-of-ltbasichttpbindinggt"></a><span data-ttu-id="43c20-102">&lt;transport&gt; de &lt;basicHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="43c20-102">&lt;transport&gt; of &lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="43c20-103">Définit les propriétés qui déterminent les paramètres d'authentification pour le transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="43c20-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
 <span data-ttu-id="43c20-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="43c20-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="43c20-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="43c20-105">\<bindings></span></span>  
<span data-ttu-id="43c20-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="43c20-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="43c20-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="43c20-107">\<binding></span></span>  
<span data-ttu-id="43c20-108">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="43c20-108">\<security></span></span>  
<span data-ttu-id="43c20-109">\<transport ></span><span class="sxs-lookup"><span data-stu-id="43c20-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43c20-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43c20-110">Syntax</span></span>  
  
```xml  
<basicHttpBinding>  
    <binding>  
        <security  
        mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
             proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string" >  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</basicHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43c20-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="43c20-111">Attributes and Elements</span></span>  
 <span data-ttu-id="43c20-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="43c20-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43c20-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="43c20-113">Attributes</span></span>  
  
|<span data-ttu-id="43c20-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="43c20-114">Attribute</span></span>|<span data-ttu-id="43c20-115">Description</span><span class="sxs-lookup"><span data-stu-id="43c20-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="43c20-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="43c20-116">clientCredentialType</span></span>|<span data-ttu-id="43c20-117">-Spécifie le type d’informations d’identification à utiliser lors de l’authentification du client à l’aide de l’authentification HTTP.</span><span class="sxs-lookup"><span data-stu-id="43c20-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="43c20-118">La valeur par défaut est `None`.</span><span class="sxs-lookup"><span data-stu-id="43c20-118">The default is `None`.</span></span> <span data-ttu-id="43c20-119">Cet attribut est de type <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="43c20-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="43c20-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="43c20-120">proxyCredentialType</span></span>|<span data-ttu-id="43c20-121">-Spécifie le type d’informations d’identification à utiliser lors de l’authentification du client à partir d’un domaine à l’aide d’un proxy sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="43c20-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="43c20-122">Cet attribut est applicable uniquement lorsque l'attribut `mode` de l'élément `security` parent est `Transport` ou `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="43c20-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="43c20-123">Cet attribut est de type <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="43c20-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="43c20-124">realm</span><span class="sxs-lookup"><span data-stu-id="43c20-124">realm</span></span>|<span data-ttu-id="43c20-125">Chaîne qui spécifie le domaine utilisé par la méthode d'authentification HTTP pour l'authentification Digest ou de base.</span><span class="sxs-lookup"><span data-stu-id="43c20-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="43c20-126">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="43c20-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="43c20-127">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="43c20-127">policyEnforcement</span></span>|<span data-ttu-id="43c20-128">Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.</span><span class="sxs-lookup"><span data-stu-id="43c20-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="43c20-129">1.  Never : la stratégie n'est jamais appliquée (la protection étendue est désactivée).</span><span class="sxs-lookup"><span data-stu-id="43c20-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="43c20-130">2.  WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.</span><span class="sxs-lookup"><span data-stu-id="43c20-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="43c20-131">3.  Always : la stratégie est toujours appliquée.</span><span class="sxs-lookup"><span data-stu-id="43c20-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="43c20-132">Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.</span><span class="sxs-lookup"><span data-stu-id="43c20-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="43c20-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="43c20-133">protectionScenario</span></span>|<span data-ttu-id="43c20-134">Cette énumération spécifie le scénario de protection appliqué par la stratégie.</span><span class="sxs-lookup"><span data-stu-id="43c20-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="43c20-135">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="43c20-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="43c20-136">Valeur</span><span class="sxs-lookup"><span data-stu-id="43c20-136">Value</span></span>|<span data-ttu-id="43c20-137">Description</span><span class="sxs-lookup"><span data-stu-id="43c20-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="43c20-138">None</span><span class="sxs-lookup"><span data-stu-id="43c20-138">None</span></span>|<span data-ttu-id="43c20-139">Les messages ne sont pas sécurisés pendant le transfert.</span><span class="sxs-lookup"><span data-stu-id="43c20-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="43c20-140">Basic</span><span class="sxs-lookup"><span data-stu-id="43c20-140">Basic</span></span>|<span data-ttu-id="43c20-141">Spécifie l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="43c20-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="43c20-142">Digest</span><span class="sxs-lookup"><span data-stu-id="43c20-142">Digest</span></span>|<span data-ttu-id="43c20-143">Spécifie l'authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="43c20-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="43c20-144">Ntlm</span><span class="sxs-lookup"><span data-stu-id="43c20-144">Ntlm</span></span>|<span data-ttu-id="43c20-145">Spécifie l'authentification NTLM le cas échéant et en cas d'échec d'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="43c20-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="43c20-146">Windows</span><span class="sxs-lookup"><span data-stu-id="43c20-146">Windows</span></span>|<span data-ttu-id="43c20-147">Spécifie l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="43c20-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="43c20-148">Attribut proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="43c20-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="43c20-149">Valeur</span><span class="sxs-lookup"><span data-stu-id="43c20-149">Value</span></span>|<span data-ttu-id="43c20-150">Description</span><span class="sxs-lookup"><span data-stu-id="43c20-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="43c20-151">Aucun.</span><span class="sxs-lookup"><span data-stu-id="43c20-151">None</span></span>|<span data-ttu-id="43c20-152">-Les messages ne sont pas sécurisés pendant le transfert.</span><span class="sxs-lookup"><span data-stu-id="43c20-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="43c20-153">Basic</span><span class="sxs-lookup"><span data-stu-id="43c20-153">Basic</span></span>|<span data-ttu-id="43c20-154">Spécifie l'authentification de base telle que définie par RFC 2617 – Authentification HTTP : Authentification de base et Digest.</span><span class="sxs-lookup"><span data-stu-id="43c20-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="43c20-155">Digest</span><span class="sxs-lookup"><span data-stu-id="43c20-155">Digest</span></span>|<span data-ttu-id="43c20-156">Spécifie l'authentification Digest telle que définie par RFC 2617 – Authentification HTTP : Authentification de base et Digest.</span><span class="sxs-lookup"><span data-stu-id="43c20-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="43c20-157">Ntlm</span><span class="sxs-lookup"><span data-stu-id="43c20-157">Ntlm</span></span>|<span data-ttu-id="43c20-158">Spécifie l'authentification NTLM le cas échéant et en cas d'échec d'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="43c20-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="43c20-159">Windows</span><span class="sxs-lookup"><span data-stu-id="43c20-159">Windows</span></span>|<span data-ttu-id="43c20-160">Spécifie l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="43c20-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="43c20-161">Certificat</span><span class="sxs-lookup"><span data-stu-id="43c20-161">Certificate</span></span>|<span data-ttu-id="43c20-162">Effectue l'authentification du client à l'aide d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="43c20-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="43c20-163">Cette option fonctionne uniquement si l'attribut `Mode` de l'élément `security` parent est configuré pour le transport et ne fonctionnera pas s'il a la valeur TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="43c20-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43c20-164">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="43c20-164">Child Elements</span></span>  
 <span data-ttu-id="43c20-165">Aucun.</span><span class="sxs-lookup"><span data-stu-id="43c20-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43c20-166">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="43c20-166">Parent Elements</span></span>  
  
|<span data-ttu-id="43c20-167">Élément</span><span class="sxs-lookup"><span data-stu-id="43c20-167">Element</span></span>|<span data-ttu-id="43c20-168">Description</span><span class="sxs-lookup"><span data-stu-id="43c20-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43c20-169">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="43c20-169">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="43c20-170">Définit les fonctionnalités de sécurité pour le [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="43c20-170">Defines the security capabilities for the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="43c20-171">Exemple</span><span class="sxs-lookup"><span data-stu-id="43c20-171">Example</span></span>  
 <span data-ttu-id="43c20-172">L’exemple suivant montre l’utilisation de la sécurité de transport SSL avec la liaison de base.</span><span class="sxs-lookup"><span data-stu-id="43c20-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="43c20-173">Par défaut, la liaison de base prend en charge la communication HTTP.</span><span class="sxs-lookup"><span data-stu-id="43c20-173">By default, the basic binding supports HTTP communication.</span></span>  
  
```xml  
<system.serviceModel>  
   <services>  
      <service   
          type="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
         <endpoint address=""  
               binding="basicHttpBinding"  
               bindingConfiguration="Binding1"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      </service>  
   </services>  
    <bindings>  
        <basicHttpBinding>  
        <!-- Configure basicHttpBinding with Transport security -- >  
        <!-- mode and clientCredentialType set to None.-->  
           <binding name="Binding1">  
               <security mode="Transport">  
                   <transport clientCredentialType="None"  
                              proxyCredentialType="None">  
                       <extendedProtectionPolicy  
                          policyEnforcement="WhenSupported"  
                          protectionScenario="TransportSelected">  
                    <customServiceNames></customServiceNames>  
                       </extendedProtectionPolicy>  
               </security>  
           </binding>  
        </basicHttpBinding>  
    </bindings>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="43c20-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43c20-174">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 [<span data-ttu-id="43c20-175">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="43c20-175">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="43c20-176">Liaisons</span><span class="sxs-lookup"><span data-stu-id="43c20-176">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="43c20-177">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="43c20-177">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="43c20-178">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="43c20-178">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="43c20-179">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="43c20-179">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
