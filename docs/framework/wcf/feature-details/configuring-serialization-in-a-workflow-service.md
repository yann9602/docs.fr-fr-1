---
title: "Configuration de la sérialisation dans un service de workflow"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9aa50b8e9f29e5dd14f0ff18d253943a73ef3a0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="b0d5b-102">Configuration de la sérialisation dans un service de workflow</span><span class="sxs-lookup"><span data-stu-id="b0d5b-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="b0d5b-103">Les services de workflow sont des services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et ont donc la possibilité d'utiliser <xref:System.Runtime.Serialization.DataContractSerializer> (le service par défaut) ou <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b0d5b-103">Workflow services are [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="b0d5b-104">Lors de l'écriture de services en dehors du workflow, le type de sérialiseur à utiliser est spécifié dans le contrat de service ou d'opération.</span><span class="sxs-lookup"><span data-stu-id="b0d5b-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="b0d5b-105">Lors de la création de services de workflow [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vous ne spécifiez pas ces contrats dans du code, mais ils sont générés au moment de l'exécution par inférence de contrat.</span><span class="sxs-lookup"><span data-stu-id="b0d5b-105">When creating [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b0d5b-106">inférence de contrat, consultez [à l’aide de contrats dans le Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="b0d5b-106"> contract inference, see  [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="b0d5b-107">Le sérialiseur est spécifié à l'aide de la propriété <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>.</span><span class="sxs-lookup"><span data-stu-id="b0d5b-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="b0d5b-108">Celle-ci peut être définie dans le concepteur comme le montre l'illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="b0d5b-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="b0d5b-109">![Définition du sérialiseur](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span><span class="sxs-lookup"><span data-stu-id="b0d5b-109">![Setting the serializer](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span></span>  
  
 <span data-ttu-id="b0d5b-110">Le sérialiseur peut également être défini dans le code, comme le montre l'exemple suivant,</span><span class="sxs-lookup"><span data-stu-id="b0d5b-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
```  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
```  
  
 <span data-ttu-id="b0d5b-111">Les types connus peuvent également être spécifiés dans des services de workflow.</span><span class="sxs-lookup"><span data-stu-id="b0d5b-111">Known types can be specified on Workflow services as well.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b0d5b-112">Connu de Types, consultez [Types connus de contrat de données](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="b0d5b-112"> Known Types see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="b0d5b-113">Les types connus peuvent être spécifiés dans le concepteur ou dans du code.</span><span class="sxs-lookup"><span data-stu-id="b0d5b-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="b0d5b-114">Pour spécifier les types courants dans le concepteur, cliquez sur le bouton de sélection en regard de la propriété KnownTypes dans la fenêtre Propriétés pour une activité <xref:System.ServiceModel.Activities.Receive>, comme le montre l'illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="b0d5b-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the properties window for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="b0d5b-115">![Propriété KnownTypes](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")</span><span class="sxs-lookup"><span data-stu-id="b0d5b-115">![KnownTypes property](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")</span></span>  
  
 <span data-ttu-id="b0d5b-116">L’Éditeur de collections de types s’affiche et vous permet de rechercher et de spécifier des types connus.</span><span class="sxs-lookup"><span data-stu-id="b0d5b-116">This will display the Type Collections Editor that will allow you to search for and specify known types.</span></span>  
  
 <span data-ttu-id="b0d5b-117">![Ajout de Types connus](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span><span class="sxs-lookup"><span data-stu-id="b0d5b-117">![Adding Known Types](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span></span>  
  
 <span data-ttu-id="b0d5b-118">Cliquez sur le **ajouter le nouveau type** lien et utilisez la liste déroulante pour sélectionner ou rechercher un type à ajouter à la collection de types connus.</span><span class="sxs-lookup"><span data-stu-id="b0d5b-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="b0d5b-119">Pour spécifier des types connus dans le code, utilisez la propriété <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A>, comme le montre l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="b0d5b-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
```  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
            approveExpense.KnownTypes.Add(typeof(Travel));  
            approveExpense.KnownTypes.Add(typeof(Meal));  
```  
  
 <span data-ttu-id="b0d5b-120">Pour voir un exemple de code complet illustrant comment configurer la sérialisation pour un service de flux de travail voir [mise en forme des messages dans les Services de Workflow](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="b0d5b-120">To see a complete code example showing how to configure serialization for a workflow service see [Formatting messages in Workflow Services](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md).</span></span>
