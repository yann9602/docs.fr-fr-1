---
title: "Comment : créer un contrat de données de base destiné à une classe ou une structure"
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
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6241df0fd5a0b6ee532691eee2279f618be25a56
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="1219b-102">Comment : créer un contrat de données de base destiné à une classe ou une structure</span><span class="sxs-lookup"><span data-stu-id="1219b-102">How to: Create a Basic Data Contract for a Class or Structure</span></span>
<span data-ttu-id="1219b-103">Cette rubrique illustre les étapes de base pour créer un contrat de données à l'aide d'une classe ou d'une structure.</span><span class="sxs-lookup"><span data-stu-id="1219b-103">This topic shows the basic steps to create a data contract using a class or structure.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="1219b-104">les contrats de données et comment elles sont utilisées, consultez [à l’aide de contrats de données](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="1219b-104"> data contracts and how they are used, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="1219b-105">Pour obtenir un didacticiel qui vous guide à travers les étapes de création d’un base [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service et le client, consultez le [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="1219b-105">For a tutorial that walks through the steps of creating a basic [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service and client, see the [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="1219b-106">Pour un exemple d’application fonctionnel qui se compose d’un service de base et un client, consultez [contrat de données de base](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span><span class="sxs-lookup"><span data-stu-id="1219b-106">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="1219b-107">Pour créer un contrat de données de base destiné à une classe ou une structure</span><span class="sxs-lookup"><span data-stu-id="1219b-107">To create a basic data contract for a class or structure</span></span>  
  
1.  <span data-ttu-id="1219b-108">Déclarez que le type a un contrat de données en appliquant l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> à la classe.</span><span class="sxs-lookup"><span data-stu-id="1219b-108">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="1219b-109">Notez que tous les types publics, y compris ceux sans attributs, sont sérialisables.</span><span class="sxs-lookup"><span data-stu-id="1219b-109">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="1219b-110">Le <xref:System.Runtime.Serialization.DataContractSerializer> déduit un contrat de données si l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> est absent.</span><span class="sxs-lookup"><span data-stu-id="1219b-110">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="1219b-111">[Types sérialisables](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="1219b-111"> [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
2.  <span data-ttu-id="1219b-112">Définissez les membres (propriétés, champs ou événements) sérialisés en appliquant l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> à chaque membre.</span><span class="sxs-lookup"><span data-stu-id="1219b-112">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="1219b-113">Ces membres sont appelés des membres de données.</span><span class="sxs-lookup"><span data-stu-id="1219b-113">These members are called data members.</span></span> <span data-ttu-id="1219b-114">Par défaut, tous les types publics sont sérialisables.</span><span class="sxs-lookup"><span data-stu-id="1219b-114">By default, all public types are serializable.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="1219b-115">[Types sérialisables](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="1219b-115"> [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1219b-116">Vous pouvez appliquer l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> aux champs privés, ce qui expose les données aux autres.</span><span class="sxs-lookup"><span data-stu-id="1219b-116">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="1219b-117">Vérifiez que le membre ne contient pas de données sensibles.</span><span class="sxs-lookup"><span data-stu-id="1219b-117">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1219b-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="1219b-118">Example</span></span>  
 <span data-ttu-id="1219b-119">L'exemple suivant montre comment créer un contrat de données pour le type `Person` en appliquant les attributs <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> à la classe et à ses membres.</span><span class="sxs-lookup"><span data-stu-id="1219b-119">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="1219b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1219b-120">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [<span data-ttu-id="1219b-121">Utilisation de contrats de données</span><span class="sxs-lookup"><span data-stu-id="1219b-121">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="1219b-122">Didacticiel Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="1219b-122">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [<span data-ttu-id="1219b-123">Prise en main</span><span class="sxs-lookup"><span data-stu-id="1219b-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
