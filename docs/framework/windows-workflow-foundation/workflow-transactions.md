---
title: "Transactions de workflow | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# Transactions de workflow
[!INCLUDE[wf1](../../../includes/wf1-md.md)] offre une prise en charge pour participer aux transactions <xref:System.Transactions> en utilisant l'activité <xref:System.Activities.Statements.TransactionScope> pour étendre une unité traitée de travail.Alors que le <xref:System.Transactions.TransactionScope?displayProperty=fullName> doit être terminé explicitement, l'activité <xref:System.Activities.Statements.TransactionScope?displayProperty=fullName> appelle implicitement la transaction une fois cette dernière terminée.Toute activité contenue dans l'élément <xref:System.Activities.Statements.TransactionScope.Body%2A> de l'activité <xref:System.Activities.Statements.TransactionScope> participe à la transaction.WF peut transférer des transactions dans un workflow en faisant appel à l'activité <xref:System.ServiceModel.Activities.TransactedReceiveScope>.Comme l'activité <xref:System.Activities.Statements.TransactionScope>, toute activité contenue dans le <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> participe à la transaction.WF vérifie que les activités dépendant de <xref:System.Transactions.Transaction.Current%2A?displayProperty=fullName> utilisent à la fois <xref:System.Activities.Statements.TransactionScope> et <xref:System.ServiceModel.Activities.TransactedReceiveScope>.Si les activités fournies par le système ne remplissent pas toutes les conditions, les activités personnalisées peuvent être construites à l'aide du <xref:System.Activities.RuntimeTransactionHandle> afin d'activer un flux avancé et des scénarios de contrôle de transaction.  
  
 Dans l'exemple suivant extrait de [Bases de TransactionScope](../../../docs/framework/windows-workflow-foundation/samples/basic-transactionscope.md), un workflow est composé d'une activité <xref:System.Activities.Statements.Sequence> qui contient des activités enfants, y compris une activité <xref:System.Activities.Statements.TransactionScope>.Les activités <xref:System.Activities.Statements.TransactionScope.Body%2A> du <xref:System.Activities.Statements.TransactionScope> s'exécutent sous la transaction initialisée par l'activité <xref:System.Activities.Statements.TransactionScope>.  
  
```csharp  
static Activity ScenarioOne()  
{  
    return new Sequence  
    {  
        Activities =  
        {  
            new WriteLine { Text = "    Begin workflow" },  
  
            new TransactionScope  
            {  
                Body = new Sequence  
                {  
                    Activities =   
                    {  
                        new WriteLine { Text = "    Begin TransactionScope" },  
  
                        new PrintTransactionId(),  
  
                        new TransactionScopeTest(),  
  
                        new WriteLine { Text = "    End TransactionScope" },  
                    },  
                },  
            },  
  
            new WriteLine { Text = "    End workflow" },  
        }  
    };  
}  
  
```  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] les exemples de [Transactions](../../../docs/framework/windows-workflow-foundation/samples/basic-transactions.md) de base et le scénario en fonction de les exemples de [Transactions](../../../docs/framework/windows-workflow-foundation/samples/transactions.md).[!INCLUDE[crdefault](../../../includes/crdefault-md.md)] sur l'utilisation de <xref:System.ServiceModel.Activities.TransactedReceiveScope>, consultez [Flux de transactions vers et depuis des services de workflow](../../../docs/framework/wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).  
  
## Voir aussi  
 <xref:System.Activities.Statements.TransactionScope>   
 <xref:System.Transactions.TransactionScope>   
 <xref:System.Transactions.Transaction.Current%2A?displayProperty=fullName>