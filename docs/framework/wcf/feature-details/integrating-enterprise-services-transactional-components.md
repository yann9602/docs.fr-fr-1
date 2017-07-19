---
title: "Int&#233;gration de composants transactionnels Enterprise Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Int&#233;gration de composants transactionnels Enterprise Services
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] offre un mécanisme permettant l'intégration automatique des composants Enterprise Services \(consultez [Intégration à des applications COM\+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)\).Cependant, vous préférez peut\-être pouvoir développer des services utilisant en interne des composants transactionnels hébergés par Enterprise Services.La fonctionnalité des transactions [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'appuyant sur l'infrastructure <xref:System.Transactions>, le processus d'intégration des composants Enterprise Services à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est identique à celui utilisé pour spécifier l'interopérabilité de <xref:System.Transactions> avec Enterprise Services, comme abordé dans [Interopérabilité des transactions COM\+ avec Enterprise Services](http://go.microsoft.com/fwlink/?LinkId=94949) \(page pouvant être en anglais\).  
  
 Afin d'offrir un niveau d'interopérabilité suffisant entre les transactions entrantes et les transactions de contexte COM\+, l'implémentation de service doit créer une instance <xref:System.Transactions.TransactionScope> et utiliser la valeur appropriée de l'énumération <xref:System.Transactions.EnterpriseServicesInteropOption>.  
  
## Intégration des composants Enterprise Services à une opération de service  
 L'exemple de code suivant contient une opération \(autorisant le transfert des transactions\) qui crée une étendue <xref:System.Transactions.TransactionScope> à l'aide de l'option <xref:System.Transactions.EnterpriseServicesInteropOption>.Les conditions suivantes s'appliquent à notre exemple :  
  
-   Si le client transfère une transaction, l'opération, y compris l'appel au composant Enterprise Services, est exécutée dans les limites de portée de cette transaction.L'utilisation de <xref:System.Transactions.EnterpriseServicesInteropOption> assure la synchronisation de la transaction avec le contexte <xref:System.EnterpriseServices>, ce qui signifie que la transaction ambiante de <xref:System.Transactions> correspond à celle de <xref:System.EnterpriseServices>.  
  
-   Si le client ne transfère pas de transaction, affecter la valeur `true` à<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> attribue une nouvelle portée de transaction à l'opération.De la même façon, l'utilisation de <xref:System.Transactions.EnterpriseServicesInteropOption> garantit que la transaction de l'opération correspond à la transaction utilisée dans le contexte du composant <xref:System.EnterpriseServices>.  
  
 Tous les appels de méthode supplémentaires se produisent également dans les limites de portée de transaction de la même opération.  
  
```  
[ServiceContract()]  
public interface ICustomerServiceContract  
{  
   [OperationContract]  
   [TransactionFlow(TransactionFlowOption.Allowed)]  
   void UpdateCustomerNameOperation(int customerID, string newCustomerName);  
}  
  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CustomerService : ICustomerServiceContract  
{  
   [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
   public void UpdateCustomerNameOperation(int customerID, string newCustomerName)  
   {  
   // Create a transaction scope with full ES interop  
      using (TransactionScope ts = new TransactionScope(  
                     TransactionScopeOption.Required,  
                     new TransactionOptions(),  
                     EnterpriseServicesInteropOption.Full))  
      {  
         // Create an Enterprise Services component  
         // Call UpdateCustomer method on an Enterprise Services   
         // component   
  
         // Call UpdateOtherCustomerData method on an Enterprise   
         // Services component   
         ts.Complete();  
      }  
  
      // Do UpdateAdditionalData on an non-Enterprise Services  
      // component  
   }  
}  
```  
  
 Si aucune synchronisation n'est requise entre la transaction en cours d'une opération et les appels aux composants transactionnels Enterprise Services, utilisez l'option <xref:System.Transactions.EnterpriseServicesInteropOption> lorsque vous instanciez l'instance <xref:System.Transactions.TransactionScope>.  
  
## Intégration des composants Enterprise Services à un client  
 L'exemple de code suivant contient un code client qui utilise une instance <xref:System.Transactions.TransactionScope> avec le paramètre <xref:System.Transactions.EnterpriseServicesInteropOption>.Dans cet exemple de code, les appels aux opérations de service qui prennent en charge le transfert des transactions se produisent dans les mêmes limites de portée de transaction que les appels aux composants Enterprise Services, leurs transactions étant identiques.  
  
```  
static void Main()  
{  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
  
    // Create a transaction scope with full ES interop  
    using (TransactionScope ts = new TransactionScope(  
          TransactionScopeOption.Required,  
          new TransactionOptions(),  
          EnterpriseServicesInteropOption.Full))  
    {  
        // Call Add calculator service operation  
  
        // Create an Enterprise Services component  
  
        // Call UpdateCustomer method on an Enterprise Services   
        // component   
  
        ts.Complete();  
    }  
  
    // Closing the client gracefully closes the connection and   
    // cleans up resources  
    client.Close();  
}  
```  
  
## Voir aussi  
 [Intégration à des applications COM\+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)   
 [Intégration à des applications COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)