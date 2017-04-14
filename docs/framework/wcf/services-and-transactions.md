---
title: "Services et transactions | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrats de service (WCF), conception de services et de transactions"
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Services et transactions
Les applications [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] peuvent initier une transaction à partir d'un client et coordonner la transaction dans l'opération de service.Les clients peuvent initier une transaction et appeler plusieurs opérations de service et s'assurer que les opérations de service sont validées ou annulées en tant qu'unité unique.  
  
 Vous pouvez activer le comportement de transaction dans le contrat de service en spécifiant un <xref:System.ServiceModel.ServiceBehaviorAttribute> et en définissant ses propriétés <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> et <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> pour les opérations de service qui requièrent des transactions clientes.Le paramètre <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> détermine si la transaction dans laquelle la méthode s'exécute est automatiquement effectuée si aucune exception non prise en charge n'est levée.[!INCLUDE[crabout](../../../includes/crabout-md.md)] ces attributs, consultez [Attributs de transaction ServiceModel](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).  
  
 Le travail effectué dans les opérations de service et géré par un gestionnaire de ressources, tel que l'enregistrement des mises à jour de base de données, fait partie de la transaction du client.  
  
 L'exemple suivant illustre l'utilisation des attributs <xref:System.ServiceModel.ServiceBehaviorAttribute> et <xref:System.ServiceModel.OperationBehaviorAttribute> pour contrôler le comportement de transaction du côté service.  
  
```  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService: ICalculatorLog  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                           TransactionAutoComplete = true)]  
    public double Add(double n1, double n2)  
    {  
        recordToLog(String.Format("Added {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                               TransactionAutoComplete = true)]  
    public double Subtract(double n1, double n2)  
    {  
        recordToLog(String.Format("Subtracted {0} from {1}", n1, n2));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                       TransactionAutoComplete = true)]  
    public double Multiply(double n1, double n2)  
    {  
        recordToLog(String.Format("Multiplied {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                       TransactionAutoComplete = true)]  
    public double Divide(double n1, double n2)  
    {  
        recordToLog(String.Format("Divided {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
}  
```  
  
 Vous pouvez activer les transactions et le flux de transactions en configurant des liaisons de client et de service pour utiliser le protocole WS\-AtomicTransaction, et affecter à l'élément [\<transactionFlow\>](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) la valeur `true`, comme illustré dans l'exemple de configuration suivant.  
  
```  
<client>  
    <endpoint address="net.tcp://localhost/ServiceModelSamples/service"   
          binding="netTcpBinding"   
          bindingConfiguration="netTcpBindingWSAT"   
          contract="Microsoft.ServiceModel.Samples.ICalculatorLog" />  
</client>  
  
<bindings>  
    <netTcpBinding>  
        <binding name="netTcpBindingWSAT"  
                transactionFlow="true"  
                transactionProtocol="WSAtomicTransactionOctober2004" />  
     </netTcpBinding>  
</bindings>  
```  
  
 Les clients peuvent commencer une transaction en créant un <xref:System.Transactions.TransactionScope> et en appelant des opérations de service dans la portée de la transaction.  
  
```  
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## Voir aussi  
 [Prise en charge transactionnelle dans System.ServiceModel](../../../docs/framework/wcf/feature-details/transactional-support-in-system-servicemodel.md)   
 [Modèles de transaction](../../../docs/framework/wcf/feature-details/transaction-models.md)   
 [WS Transaction Flow](../../../docs/framework/wcf/samples/ws-transaction-flow.md)