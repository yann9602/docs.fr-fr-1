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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f8138fb94de953f133ab21cc2320e0914bc380fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-serialization-in-a-workflow-service"></a>Configuration de la sérialisation dans un service de workflow
Les services de workflow sont des services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et ont donc la possibilité d'utiliser <xref:System.Runtime.Serialization.DataContractSerializer> (le service par défaut) ou <xref:System.Xml.Serialization.XmlSerializer>. Lors de l'écriture de services en dehors du workflow, le type de sérialiseur à utiliser est spécifié dans le contrat de service ou d'opération. Lors de la création de services de workflow [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vous ne spécifiez pas ces contrats dans du code, mais ils sont générés au moment de l'exécution par inférence de contrat. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]inférence de contrat, consultez [à l’aide de contrats dans le Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).  Le sérialiseur est spécifié à l'aide de la propriété <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>. Celle-ci peut être définie dans le concepteur comme le montre l'illustration suivante.  
  
 ![Définition du sérialiseur](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")  
  
 Le sérialiseur peut également être défini dans le code, comme le montre l'exemple suivant,  
  
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
  
 Les types connus peuvent également être spécifiés dans des services de workflow. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Connu de Types, consultez [Types connus de contrat de données](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). Les types connus peuvent être spécifiés dans le concepteur ou dans du code. Pour spécifier les types courants dans le concepteur, cliquez sur le bouton de sélection en regard de la propriété KnownTypes dans la fenêtre Propriétés pour une activité <xref:System.ServiceModel.Activities.Receive>, comme le montre l'illustration suivante.  
  
 ![Propriété KnownTypes](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")  
  
 L’Éditeur de collections de types s’affiche et vous permet de rechercher et de spécifier des types connus.  
  
 ![Ajout de Types connus](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")  
  
 Cliquez sur le **ajouter le nouveau type** lien et utilisez la liste déroulante pour sélectionner ou rechercher un type à ajouter à la collection de types connus. Pour spécifier des types connus dans le code, utilisez la propriété <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A>, comme le montre l'exemple suivant :  
  
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
  
 Pour voir un exemple de code complet illustrant comment configurer la sérialisation pour un service de flux de travail voir [mise en forme des messages dans les Services de Workflow](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md).
