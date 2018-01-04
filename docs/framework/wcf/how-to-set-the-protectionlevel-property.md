---
title: "Comment : définir la propriété ProtectionLevel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9b90df85259dfe48f071ca2b4b8404cfe8e673e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-protectionlevel-property"></a><span data-ttu-id="b3779-102">Comment : définir la propriété ProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="b3779-102">How to: Set the ProtectionLevel Property</span></span>
<span data-ttu-id="b3779-103">Vous pouvez définir le niveau de protection en appliquant un attribut approprié et en définissant la propriété.</span><span class="sxs-lookup"><span data-stu-id="b3779-103">You can set the protection level by applying an appropriate attribute and setting the property.</span></span> <span data-ttu-id="b3779-104">Vous pouvez définir la protection au niveau du service afin d'affecter toutes les parties de chaque message, ou vous pouvez la définir à des niveaux de plus en plus spécifiques, des méthodes aux parties du message.</span><span class="sxs-lookup"><span data-stu-id="b3779-104">You can set protection at the service level to affect all parts of every message, or you can set protection at increasingly granular levels, from methods to message parts.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="b3779-105">le `ProtectionLevel` propriété, consultez [au niveau de Protection de présentation](../../../docs/framework/wcf/understanding-protection-level.md).</span><span class="sxs-lookup"><span data-stu-id="b3779-105"> the `ProtectionLevel` property, see [Understanding Protection Level](../../../docs/framework/wcf/understanding-protection-level.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3779-106">Vous pouvez définir des niveaux de protection dans le code uniquement, mais pas dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="b3779-106">You can set protection levels only in code, not in configuration.</span></span>  
  
### <a name="to-sign-all-messages-for-a-service"></a><span data-ttu-id="b3779-107">Pour signer tous les messages d'un service</span><span class="sxs-lookup"><span data-stu-id="b3779-107">To sign all messages for a service</span></span>  
  
1.  <span data-ttu-id="b3779-108">Créez une interface pour le service.</span><span class="sxs-lookup"><span data-stu-id="b3779-108">Create an interface for the service.</span></span>  
  
2.  <span data-ttu-id="b3779-109">Appliquez l'attribut <xref:System.ServiceModel.ServiceContractAttribute> au service et affectez <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> à la propriété <xref:System.Net.Security.ProtectionLevel.Sign>, tel qu'indiqué dans le code suivant (le niveau par défaut est <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span><span class="sxs-lookup"><span data-stu-id="b3779-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the service and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code (the default level is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span></span>  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a><span data-ttu-id="b3779-110">Pour signer toutes les parties de message d'une opération</span><span class="sxs-lookup"><span data-stu-id="b3779-110">To sign all message parts for an operation</span></span>  
  
1.  <span data-ttu-id="b3779-111">Créez une interface pour le service et appliquez l'attribut <xref:System.ServiceModel.ServiceContractAttribute> à celle-ci.</span><span class="sxs-lookup"><span data-stu-id="b3779-111">Create an interface for the service and apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
2.  <span data-ttu-id="b3779-112">Ajoutez une déclaration de méthode à l'interface.</span><span class="sxs-lookup"><span data-stu-id="b3779-112">Add a method declaration to the interface.</span></span>  
  
3.  <span data-ttu-id="b3779-113">Appliquez l'attribut <xref:System.ServiceModel.OperationContractAttribute> à la méthode et affectez <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> à la propriété <xref:System.Net.Security.ProtectionLevel.Sign>, tel qu'indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b3779-113">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to the method, and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a><span data-ttu-id="b3779-114">Protection des messages d'erreur</span><span class="sxs-lookup"><span data-stu-id="b3779-114">Protecting Fault Messages</span></span>  
 <span data-ttu-id="b3779-115">Les exceptions levées sur un service peuvent être envoyées à un client en tant qu'erreurs SOAP.</span><span class="sxs-lookup"><span data-stu-id="b3779-115">Exceptions that are thrown on a service can be sent to a client as SOAP faults.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="b3779-116">Création de fortement typée erreurs, consultez [spécification et gestion des erreurs dans les contrats et les Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) et [Comment : déclarer des erreurs dans les contrats de Service](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="b3779-116"> creating strongly typed faults, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) and [How to: Declare Faults in Service Contracts](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md).</span></span>  
  
#### <a name="to-protect-a-fault-message"></a><span data-ttu-id="b3779-117">Pour protéger un message d'erreur</span><span class="sxs-lookup"><span data-stu-id="b3779-117">To protect a fault message</span></span>  
  
1.  <span data-ttu-id="b3779-118">Créez un type qui représente le message d'erreur.</span><span class="sxs-lookup"><span data-stu-id="b3779-118">Create a type that represents the fault message.</span></span> <span data-ttu-id="b3779-119">L'exemple suivant crée une classe appelée `MathFault` contenant deux champs.</span><span class="sxs-lookup"><span data-stu-id="b3779-119">The following example creates a class named `MathFault` with two fields.</span></span>  
  
2.  <span data-ttu-id="b3779-120">Appliquez l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> au type et un attribut <xref:System.Runtime.Serialization.DataMemberAttribute> à chaque champ qui doit être sérialisé, tel qu'indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b3779-120">Apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type and a <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each field that should be serialized, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3.  <span data-ttu-id="b3779-121">Dans l'interface qui retournera l'erreur, appliquez l'attribut <xref:System.ServiceModel.FaultContractAttribute> à la méthode que retournera l'erreur et affectez le type de la classe d'erreur au paramètre `detailType`.</span><span class="sxs-lookup"><span data-stu-id="b3779-121">In the interface that will return the fault, apply the <xref:System.ServiceModel.FaultContractAttribute> attribute to the method that will return the fault and set the `detailType` parameter to the type of the fault class.</span></span>  
  
4.  <span data-ttu-id="b3779-122">Également dans le constructeur, affectez <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> à la propriété <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, tel qu'indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b3779-122">Also in the constructor, set the <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a><span data-ttu-id="b3779-123">Protection de parties de message</span><span class="sxs-lookup"><span data-stu-id="b3779-123">Protecting Message Parts</span></span>  
 <span data-ttu-id="b3779-124">Utilisez un contrat de message pour protéger des parties d'un message.</span><span class="sxs-lookup"><span data-stu-id="b3779-124">Use a message contract to protect parts of a message.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="b3779-125">contrats de message, consultez [à l’aide de contrats de Message](../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="b3779-125"> message contracts, see [Using Message Contracts](../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span></span>  
  
#### <a name="to-protect-a-message-body"></a><span data-ttu-id="b3779-126">Pour protéger le corps d'un message</span><span class="sxs-lookup"><span data-stu-id="b3779-126">To protect a message body</span></span>  
  
1.  <span data-ttu-id="b3779-127">Créez un type qui représente le message.</span><span class="sxs-lookup"><span data-stu-id="b3779-127">Create a type that represents the message.</span></span> <span data-ttu-id="b3779-128">L'exemple suivant crée une classe `Company` contenant deux champs, `CompanyName` et `CompanyID`.</span><span class="sxs-lookup"><span data-stu-id="b3779-128">The following example creates a `Company` class with two fields, `CompanyName` and `CompanyID`.</span></span>  
  
2.  <span data-ttu-id="b3779-129">Appliquez l'attribut <xref:System.ServiceModel.MessageContractAttribute> à la classe et affectez <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> à la propriété <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="b3779-129">Apply the <xref:System.ServiceModel.MessageContractAttribute> attribute to the class and set the <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
3.  <span data-ttu-id="b3779-130">Appliquez l'attribut <xref:System.ServiceModel.MessageHeaderAttribute> à un champ qui sera exprimé sous forme d'un en-tête de message et affectez `ProtectionLevel` à la propriété <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="b3779-130">Apply the <xref:System.ServiceModel.MessageHeaderAttribute> attribute to a field that will be expressed as a message header and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
4.  <span data-ttu-id="b3779-131">Appliquer le <xref:System.ServiceModel.MessageBodyMemberAttribute> à n’importe quel champ qui sera exprimé en tant que partie du corps du message et définir le `ProtectionLevel` propriété <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b3779-131">Apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to any field that will be expressed as part of the message body, and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following example.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="b3779-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="b3779-132">Example</span></span>  
 <span data-ttu-id="b3779-133">L'exemple suivant définit la propriété `ProtectionLevel` de plusieurs classes d'attributs à divers emplacements dans un service.</span><span class="sxs-lookup"><span data-stu-id="b3779-133">The following example sets the `ProtectionLevel` property of several attribute classes at various places in a service.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b3779-134">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="b3779-134">Compiling the Code</span></span>  
 <span data-ttu-id="b3779-135">Le code suivant présente les espaces de noms requis pour compiler l'exemple de code.</span><span class="sxs-lookup"><span data-stu-id="b3779-135">The following code shows the namespaces required to compile the example code.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="b3779-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3779-136">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.ServiceModel.MessageContractAttribute>  
 <xref:System.ServiceModel.MessageBodyMemberAttribute>  
 [<span data-ttu-id="b3779-137">Présentation du niveau de protection</span><span class="sxs-lookup"><span data-stu-id="b3779-137">Understanding Protection Level</span></span>](../../../docs/framework/wcf/understanding-protection-level.md)
