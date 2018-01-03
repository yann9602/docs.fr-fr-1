---
title: '&lt;netNamedPipeBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f5bf4a933928770744e8974b5bb20ef06f18c93
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltnetnamedpipebindinggt"></a><span data-ttu-id="43706-102">&lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="43706-102">&lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="43706-103">Définit une liaison qui est sécurisée, fiable, optimisée pour la communication interprocessus sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="43706-103">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="43706-104">Par défaut, elle génère une pile de communication du runtime avec WS-ReliableMessaging pour la fiabilité, la sécurité du transport pour la sécurité du transfert, des canaux nommés pour la remise de messages et l'encodage binaire de messages.</span><span class="sxs-lookup"><span data-stu-id="43706-104">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
 <span data-ttu-id="43706-105">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="43706-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="43706-106">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="43706-106">\<bindings></span></span>  
<span data-ttu-id="43706-107">\<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="43706-107">\<netNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43706-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43706-108">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding   
      closeTimeout="TimeSpan"  
      hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
      maxBufferPoolSize="Integer"  
      maxBufferSize="Integer"  
      maxConnections="Integer"   
      maxReceivedMessageSize="Integer"  
            name="string"  
      openTimeout="TimeSpan"   
      receiveTimeout="TimeSpan"  
      sendTimeout="TimeSpan"  
      transactionFlow="Boolean"  
      transactionProtocol="OleTransactions/WS-AtomicTransactionOctober2004"  
            transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
      <security mode="None/Transport">  
            <transport  protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43706-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="43706-109">Attributes and Elements</span></span>  
 <span data-ttu-id="43706-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="43706-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43706-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="43706-111">Attributes</span></span>  
  
|<span data-ttu-id="43706-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="43706-112">Attribute</span></span>|<span data-ttu-id="43706-113">Description</span><span class="sxs-lookup"><span data-stu-id="43706-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="43706-114">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="43706-114">closeTimeout</span></span>|<span data-ttu-id="43706-115"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="43706-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="43706-116">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="43706-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="43706-117">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="43706-117">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="43706-118">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="43706-118">hostnameComparisonMode</span></span>|<span data-ttu-id="43706-119">Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI.</span><span class="sxs-lookup"><span data-stu-id="43706-119">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="43706-120">Cet attribut est de type `System.ServiceModel.HostnameComparisonMode`, ce qui indique si le nom d'hôte est utilisé pour atteindre le service en cas de correspondance sur l'URI.</span><span class="sxs-lookup"><span data-stu-id="43706-120">This attribute is of type `System.ServiceModel.HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="43706-121">La valeur par défaut est `StrongWildcard`, qui ignore le nom d'hôte dans la correspondance.</span><span class="sxs-lookup"><span data-stu-id="43706-121">The default value is `StrongWildcard`, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="43706-122">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="43706-122">maxBufferPoolSize</span></span>|<span data-ttu-id="43706-123">Entier qui spécifie la taille maximale du pool de mémoires tampons pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="43706-123">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="43706-124">La valeur par défaut est 524 288 octets (512 x 1024).</span><span class="sxs-lookup"><span data-stu-id="43706-124">The default is 524,288 bytes (512 * 1024).</span></span> <span data-ttu-id="43706-125">De nombreuses parties de Windows Communication Foundation (WCF) utilisent des mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="43706-125">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="43706-126">La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage.</span><span class="sxs-lookup"><span data-stu-id="43706-126">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="43706-127">Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="43706-127">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="43706-128">Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.</span><span class="sxs-lookup"><span data-stu-id="43706-128">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="43706-129">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="43706-129">maxBufferSize</span></span>|<span data-ttu-id="43706-130">Entier positif qui spécifie la taille maximale, en octets, de la mémoire tampon utilisée pour stocker des messages en mémoire.</span><span class="sxs-lookup"><span data-stu-id="43706-130">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="43706-131">Si la mémoire tampon est pleine, les données excédentaires restent dans le socket sous-jacent jusqu'à ce que de l'espace disponible se libère dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="43706-131">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="43706-132">Cette valeur ne peut pas être inférieure à l'attribut `maxReceivedMessageSize`.</span><span class="sxs-lookup"><span data-stu-id="43706-132">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="43706-133">La valeur par défaut est 65536.</span><span class="sxs-lookup"><span data-stu-id="43706-133">The default is 65536.</span></span> <span data-ttu-id="43706-134">Pour plus d'informations, consultez <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="43706-134">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="43706-135">maxConnections</span><span class="sxs-lookup"><span data-stu-id="43706-135">maxConnections</span></span>|<span data-ttu-id="43706-136">Entier qui spécifie le nombre maximal de connexions sortantes et entrantes que le service créera/acceptera.</span><span class="sxs-lookup"><span data-stu-id="43706-136">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="43706-137">Les connexions entrantes et sortantes sont comptées par rapport à une limite distincte spécifiée par cet attribut.</span><span class="sxs-lookup"><span data-stu-id="43706-137">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="43706-138">Les connexions entrantes dépassant cette limite sont mises en file d'attente jusqu'à ce que de l'espace soit disponible sous cette limite.</span><span class="sxs-lookup"><span data-stu-id="43706-138">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="43706-139">Les connexions sortantes dépassant cette limite sont mises en file d'attente jusqu'à ce que de l'espace soit disponible sous cette limite.</span><span class="sxs-lookup"><span data-stu-id="43706-139">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="43706-140">La valeur par défaut est 10.</span><span class="sxs-lookup"><span data-stu-id="43706-140">The default is 10.</span></span>|  
|<span data-ttu-id="43706-141">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="43706-141">maxReceivedMessageSize</span></span>|<span data-ttu-id="43706-142">Entier positif qui spécifie la taille maximale du message, en octets, y compris les en-têtes, pouvant être reçu sur un canal configuré avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="43706-142">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="43706-143">L'expéditeur d'un message qui dépasse cette limite se verra notifier une erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="43706-143">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="43706-144">Ce dernier abandonne le message et crée une entrée d'événement dans le journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="43706-144">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="43706-145">La valeur par défaut est 65536.</span><span class="sxs-lookup"><span data-stu-id="43706-145">The default is 65536.</span></span>|  
|<span data-ttu-id="43706-146">name</span><span class="sxs-lookup"><span data-stu-id="43706-146">name</span></span>|<span data-ttu-id="43706-147">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="43706-147">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="43706-148">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="43706-148">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="43706-149">Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d'avoir un nom.</span><span class="sxs-lookup"><span data-stu-id="43706-149">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="43706-150">Pour plus d’informations sur la configuration par défaut et nommées liaisons et comportements, consultez [Configuration simplifiée](../../../../../docs/framework/wcf/simplified-configuration.md) et [simplifié la Configuration des Services WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="43706-150">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="43706-151">openTimeout</span><span class="sxs-lookup"><span data-stu-id="43706-151">openTimeout</span></span>|<span data-ttu-id="43706-152"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="43706-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="43706-153">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="43706-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="43706-154">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="43706-154">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="43706-155">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="43706-155">receiveTimeout</span></span>|<span data-ttu-id="43706-156"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="43706-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="43706-157">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="43706-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="43706-158">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="43706-158">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="43706-159">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="43706-159">sendTimeout</span></span>|<span data-ttu-id="43706-160"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="43706-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="43706-161">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="43706-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="43706-162">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="43706-162">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="43706-163">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="43706-163">transactionFlow</span></span>|<span data-ttu-id="43706-164">Valeur booléenne qui spécifie si la liaison prend en charge le flux WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="43706-164">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="43706-165">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="43706-165">The default is `false`.</span></span>|  
|<span data-ttu-id="43706-166">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="43706-166">transactionProtocol</span></span>|<span data-ttu-id="43706-167">Spécifie le protocole de transaction à utiliser avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="43706-167">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="43706-168">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="43706-168">Valid values are</span></span><br /><br /> <span data-ttu-id="43706-169">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="43706-169">-   OleTransactions</span></span><br /><span data-ttu-id="43706-170">WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="43706-170">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="43706-171">La valeur par défaut est OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="43706-171">The default is OleTransactions.</span></span> <span data-ttu-id="43706-172">Cet attribut est de type <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="43706-172">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="43706-173">transferMode</span><span class="sxs-lookup"><span data-stu-id="43706-173">transferMode</span></span>|<span data-ttu-id="43706-174">Valeur <xref:System.ServiceModel.TransferMode> qui spécifie si les messages sont mis en mémoire tampon ou transmis en continu ou s'il s'agit d'une demande ou d'une réponse.</span><span class="sxs-lookup"><span data-stu-id="43706-174">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43706-175">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="43706-175">Child Elements</span></span>  
  
|<span data-ttu-id="43706-176">Élément</span><span class="sxs-lookup"><span data-stu-id="43706-176">Element</span></span>|<span data-ttu-id="43706-177">Description</span><span class="sxs-lookup"><span data-stu-id="43706-177">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43706-178">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="43706-178">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="43706-179">Définit les paramètres de sécurité de la liaison.</span><span class="sxs-lookup"><span data-stu-id="43706-179">Defines the security settings for the binding.</span></span> <span data-ttu-id="43706-180">Cet élément est de type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="43706-180">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|[<span data-ttu-id="43706-181">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="43706-181">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="43706-182">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="43706-182">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="43706-183">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="43706-183">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="43706-184">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="43706-184">Parent Elements</span></span>  
  
|<span data-ttu-id="43706-185">Élément</span><span class="sxs-lookup"><span data-stu-id="43706-185">Element</span></span>|<span data-ttu-id="43706-186">Description</span><span class="sxs-lookup"><span data-stu-id="43706-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43706-187">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="43706-187">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="43706-188">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="43706-188">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43706-189">Notes</span><span class="sxs-lookup"><span data-stu-id="43706-189">Remarks</span></span>  
 <span data-ttu-id="43706-190">`NetNamedPipeBinding` génère par défaut une pile de communication au moment de l'exécution, qui utilise la sécurité de transport, des canaux nommés pour la remise des messages et un encodage de message binaire.</span><span class="sxs-lookup"><span data-stu-id="43706-190">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="43706-191">Cette liaison est une solution fournie par le système WCF (Windows Communication Foundation) adaptée à la communication sur les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="43706-191">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="43706-192">Elle prend en outre en charge des transactions.</span><span class="sxs-lookup"><span data-stu-id="43706-192">It also supports transactions.</span></span>  
  
 <span data-ttu-id="43706-193">La configuration par défaut de `NetNamedPipeBinding` est similaire à celle fournie par `NetTcpBinding`, mais en plus simple, car l'implémentation de WCF est uniquement destinée à être utilisée sur un ordinateur, de sorte qu'il y a moins de fonctionnalités exposées.</span><span class="sxs-lookup"><span data-stu-id="43706-193">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="43706-194">La différence la plus notable est que le paramètre `securityMode` offre uniquement les options `None` et `Transport`.</span><span class="sxs-lookup"><span data-stu-id="43706-194">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="43706-195">La prise en charge de la sécurité SOAP ne fait pas partie des options incluses.</span><span class="sxs-lookup"><span data-stu-id="43706-195">SOAP security support is not an included option.</span></span> <span data-ttu-id="43706-196">Le comportement de sécurité est configurable à l'aide de l'attribut facultatif `securityMode`.</span><span class="sxs-lookup"><span data-stu-id="43706-196">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43706-197">Exemple</span><span class="sxs-lookup"><span data-stu-id="43706-197">Example</span></span>  
 <span data-ttu-id="43706-198">L’exemple suivant montre la liaison netNamedPipeBinding, qui fournit la communication interprocessus sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="43706-198">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="43706-199">Les canaux nommés ne fonctionnent pas sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="43706-199">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="43706-200">La liaison est spécifiée dans les fichiers de configuration pour le client et le service.</span><span class="sxs-lookup"><span data-stu-id="43706-200">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="43706-201">Le type de liaison est spécifié dans l'attribut `binding` de l'élément `<endpoint>`.</span><span class="sxs-lookup"><span data-stu-id="43706-201">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="43706-202">Si vous souhaitez configurer la liaison netNamedPipeBinding et modifier quelques-uns de ses paramètres, vous devez définir une configuration de liaison.</span><span class="sxs-lookup"><span data-stu-id="43706-202">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="43706-203">Le point de terminaison doit référencer la configuration de liaison par nom avec un attribut `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="43706-203">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="43706-204">Dans cet exemple, la configuration de liaison est nommée Binding1.</span><span class="sxs-lookup"><span data-stu-id="43706-204">In this example, the binding configuration is named Binding1.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <!-- this endpoint is exposed at the base address provided by host: net.pipe://localhost/ServiceModelSamples/service  -->  
        <endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
                  binding="netNamedPipeBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <bindings>  
      <netNamedPipeBinding>  
        <binding   
                 closeTimeout="00:01:00"  
                 openTimeout="00:01:00"   
                 receiveTimeout="00:10:00"   
                 sendTimeout="00:01:00"  
                 transactionFlow="false"   
                 transferMode="Buffered"   
                 transactionProtocol="OleTransactions"  
                 hostNameComparisonMode="StrongWildcard"   
                 maxBufferPoolSize="524288"  
                 maxBufferSize="65536"   
                 maxConnections="10"   
                 maxReceivedMessageSize="65536">  
          <security mode="Transport">  
            <transport protectionLevel="EncryptAndSign" />  
          </security>  
        </binding>  
      </netNamedPipeBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="43706-205">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43706-205">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>  
 <xref:System.ServiceModel.NetNamedPipeBinding>  
 [<span data-ttu-id="43706-206">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="43706-206">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="43706-207">Liaisons</span><span class="sxs-lookup"><span data-stu-id="43706-207">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="43706-208">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="43706-208">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="43706-209">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="43706-209">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)
