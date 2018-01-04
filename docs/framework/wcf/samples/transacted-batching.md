---
title: Transacted Batching
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecd328ed-332e-479c-a894-489609bcddd2
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87d8e3e09618b214dcafb7afd82970dde54fc4fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="transacted-batching"></a>Transacted Batching
Cet exemple montre comment traiter les lectures transactionnelles à l'aide de Message Queuing (MSMQ). Le traitement transactionnel par lots est une fonctionnalité d'optimisation des performances pour les lectures transactionnelles dans les communications mises en file d'attente.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Dans le cadre d'une communication en file d'attente, le client communique avec le service à l'aide d'une file d'attente. Cela signifie que le client envoie ses messages à cette file d'attente. Le service reçoit des messages de la file d'attente. Par conséquent, dans le cadre d'une communication en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément.  
  
 Cet exemple illustre le traitement transactionnel par lots. Le traitement transactionnel par lots est un comportement qui permet l'utilisation d'une transaction unique lors de la lecture de nombreux messages dans la file d'attente et leur traitement.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Si le service est exécuté en premier, il vérifie que la file d'attente existe. Si la file d'attente n'existe pas, le service en crée une. Vous pouvez exécuter le service en premier pour créer la file d'attente, ou en créer une à l'aide du Gestionnaire de files d'attente MSMQ. Procédez comme suit pour créer une file d'attente dans Windows 2008 :  
  
    1.  Ouvrez le Gestionnaire de serveur dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Développez le **fonctionnalités** onglet.  
  
    3.  Avec le bouton droit **files d’attente de messages privées**, puis sélectionnez **nouveau**, **file d’attente privée**.  
  
    4.  Vérifiez le **transactionnel** boîte.  
  
    5.  Entrez `ServiceModelSamplesTransacted` comme nom de la nouvelle file d’attente.  
  
    > [!NOTE]
    >  Dans cet exemple, le client envoie des centaines de messages dans le cadre du lot. Le traitement de ces messages par l'application du service peut prendre un certain temps.  
  
3.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Pour exécuter l'exemple sur un ordinateur joint à un groupe de travail ou sans intégration Active Directory  
  
1.  Avec <xref:System.ServiceModel.NetMsmqBinding>, la sécurité du transport est activée par défaut. Il existe deux propriétés pertinentes pour la sécurité de transport MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> et <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` par défaut, le mode d’authentification a la valeur `Windows` et le niveau de protection a la valeur `Sign`. Pour que MSMQ fournisse la fonctionnalité d’authentification et de signature, il doit faire partie d’un domaine et l’option d’intégration d’Active Directory doit être installée pour MSMQ. Si vous exécutez cet exemple sur un ordinateur qui ne satisfait pas ces critères vous recevez une erreur.  
  
2.  Si votre ordinateur ne fait pas partie d'un domaine ou ne dispose pas de l'intégration Active Directory, désactivez la sécurité de transport en affectant au mode d'authentification et niveau de protection la valeur `None` comme indiqué dans l'exemple de configuration suivant :  
  
    ```xml  
    <system.serviceModel>  
      <behaviors>  
        <serviceBehaviors>  
          <behavior name="ThrottlingBehavior">  
            <serviceMetadata httpGetEnabled="true"/>  
            <serviceThrottling maxConcurrentCalls="5"/>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="BatchingBehavior">  
            <transactedBatching maxBatchSize="100"/>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <services>  
        <service   
            behaviorConfiguration="ThrottlingBehavior"   
            name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                    binding="netMsmqBinding"  
                    bindingConfiguration="Binding1"   
                    behaviorConfiguration="BatchingBehavior"   
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          <endpoint address="mex"  
                    binding="mexHttpBinding"  
                    contract="IMetadataExchange" />  
        </service>  
      </services>  
  
      <bindings>  
        <netMsmqBinding>  
          <binding name="Binding1">  
            <security mode="None" />  
          </binding>  
        </netMsmqBinding>  
      </bindings>  
  
    </system.serviceModel>  
    ```  
  
3.  Assurez-vous de modifier la configuration sur le serveur et le client avant d'exécuter l'exemple.  
  
    > [!NOTE]
    >  L'affectation de `security``mode` à `None` revient à affecter <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> à la sécurité <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, `Message` et `None`.  
  
4.  Pour exécuter la base de données sur un ordinateur distant, modifiez la chaîne de connexion pour qu'elle pointe vers l'ordinateur sur lequel se trouve la base de données.  
  
## <a name="requirements"></a>Configuration requise  
 Pour exécuter cet exemple, MSMQ doit être installé et SQL ou SQL Express est requis.  
  
## <a name="demonstrates"></a>Démonstrations  
 L'exemple montre le comportement du traitement transactionnel par lots. Le traitement transactionnel par lots est une fonctionnalité d'optimisation des performances fournie le transport de mise en file d'attente MSMQ.  
  
 Lorsque les transactions sont utilisées pour envoyer et recevoir des messages il y a en fait 2 transactions distinctes. Lorsque le client envoie des messages dans l'étendue d'une transaction, la transaction est locale au client et au gestionnaire de files d'attente client. Lorsque le service reçoit des messages dans l'étendue de la transaction, la transaction est locale au service et au gestionnaire de files d'attente de réception. N'oubliez pas que le client et le service ne participent pas à la même transaction : ils utilisent des transactions différentes lorsqu'ils effectuent leurs opérations (comme l'envoi et la réception) avec la file d'attente.  
  
 Dans cet exemple, nous utilisons une transaction unique pour l'exécution de plusieurs opérations de service. Elle est utilisée uniquement en tant que fonctionnalité d’optimisation des performances et ne concerne pas la sémantique de l’application. L’exemple est basé sur [transactionnel de liaison MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).  
  
## <a name="comments"></a>Commentaires  
 Dans cet exemple, le client envoie un lot de messages au service à partir de l'étendue d'une transaction. Pour afficher l'optimisation des performances, nous envoyons un grand nombre de messages ; dans ce cas, jusqu'à 2 500 messages.  
  
 Les messages envoyés à la file d'attente sont ensuite reçus par le service dans l'étendue de la transaction définie par le service. Sans traitement par lots, cela provoque 2 500 transactions pour chaque appel de l'opération de service. Ceci influe sur les performances du système. Étant donné que deux gestionnaires des ressources sont impliqués (la file d'attente MSMQ et la base de données `Orders`), chaque transaction est une transaction DTC. Nous optimisons ceci par l'utilisation d'un nombre bien moins important de transactions en garantissant qu'un lot de messages et que les appels d'opération de service aient lieu dans la même transaction.  
  
 Pour utiliser la fonctionnalité de traitement par lots, il faut :  
  
-   indiquer le comportement du traitement transactionnel par lots dans la configuration ;  
  
-   indiquer la taille de lot en nombre de messages devant être lus au cours d'une transaction ;  
  
-   indiquer le nombre maximal de lots simultanés à exécuter.  
  
 Dans cet exemple, nous affichons les gains de performance par la réduction du nombre de transactions en garantissant que 100 opérations de service sont appelées dans une même transaction avant de valider la transaction.  
  
 Le comportement de service définit un comportement d'opération avec la valeur `TransactionScopeRequired` affectée à `true`. Ainsi, l'étendue de transaction qui est utilisée pour récupérer le message de la file d'attente est utilisée par tous les gestionnaires des ressources auxquels accède la méthode. Dans cet exemple, nous utilisons une base de données classique pour stocker les informations de commande fournisseur contenues dans le message. L'étendue de transaction garantie également que si la méthode lève une exception, le message est renvoyé dans la file d'attente. Sans définir ce comportement d'opération, un canal mis en file d'attente crée une transaction pour lire le message à partir de la file d'attente et le valide automatiquement avant qu'il soit distribué afin que si l'opération échoue, le message soit perdu. Dans la plupart des cas, les opérations de service s'inscrivent dans la transaction utilisée pour lire le message à partir de la file d'attente, comme indiqué dans le code suivant.  
  
 Notez que `ReleaseServiceInstanceOnTransactionComplete` a la valeur `false`. C'est une spécification importante pour le traitement par lots. La propriété `ReleaseServiceInstanceOnTransactionComplete` sur `ServiceBehaviorAttribute` indique que faire avec l'instance de service une fois la transaction terminée. Par défaut, l'instance de service est diffusée lorsque la transaction est terminée. La principale particularité du traitement par lots est l'utilisation d'une seule transaction pour lire et distribuer de nombreux messages dans la file d'attente. Par conséquent, la diffusion de l'instance de service provoque par conséquent la fin prématurée de la transaction, empêchant l'utilisation du traitement par lots. Si cette propriété a la valeur `true` et que le comportement du traitement transactionnel par lots est ajouté au point de terminaison, le comportement de la validation du traitement par lots lève une exception.  
  
```  
// Service class that implements the service contract.  
// Added code to write output to the console window.  
[ServiceBehavior(ReleaseServiceInstanceOnTransactionComplete=false,   
TransactionIsolationLevel=  
System.Transactions.IsolationLevel.Serializable, ConcurrencyMode=ConcurrencyMode.Multiple)]  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                       TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
    }  
    …  
}  
```  
  
 La classe `Orders` encapsule le traitement de la commande. Dans cet exemple, elle met à jour la base de données avec les informations du bon de commande.  
  
```  
// Order Processing Logic  
public class Orders  
{  
    public static void Add(PurchaseOrder po)  
    {  
        // Insert purchase order.  
        SqlCommand insertPurchaseOrderCommand =   
        new SqlCommand(  
        "insert into PurchaseOrders(poNumber, customerId)   
                               values(@poNumber, @customerId)");  
        insertPurchaseOrderCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        insertPurchaseOrderCommand.Parameters.Add("@customerId",   
                                         SqlDbType.VarChar, 50);  
  
        // Insert product line item.  
        SqlCommand insertProductLineItemCommand =   
             new SqlCommand("insert into ProductLineItems(productId,   
                    unitCost, quantity, poNumber) values(@productId,   
                    @unitCost, @quantity, @poNumber)");  
        insertProductLineItemCommand.Parameters.Add("@productId",   
                                           SqlDbType.VarChar, 50);  
        insertProductLineItemCommand.Parameters.Add("@unitCost",   
                                                  SqlDbType.Float);  
        insertProductLineItemCommand.Parameters.Add("@quantity",   
                                                     SqlDbType.Int);  
        insertProductLineItemCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        int rowsAffected = 0;  
        using (TransactionScope scope =   
              new TransactionScope(TransactionScopeOption.Required))  
        {  
             using (SqlConnection conn = new   
                 SqlConnection(  
                 ConfigurationManager.AppSettings["connectionString"]))  
             {  
                 conn.Open();  
  
                // Insert into purchase order table.  
               insertPurchaseOrderCommand.Connection = conn;  
               insertPurchaseOrderCommand.Parameters["@poNumber"].Value   
                                                       = po.PONumber;  
             insertPurchaseOrderCommand.Parameters["@customerId"].Value   
                                                    =po.CustomerId;  
             insertPurchaseOrderCommand.ExecuteNonQuery();  
  
            // Insert into product line item table.  
            insertProductLineItemCommand.Connection = conn;  
            foreach (PurchaseOrderLineItem orderLineItem in   
                                        po.orderLineItems) {  
            insertProductLineItemCommand.Parameters["@poNumber"].Value   
                                                          =po.PONumber;  
            insertProductLineItemCommand.Parameters["@productId"].Value   
                                             = orderLineItem.ProductId;  
            insertProductLineItemCommand.Parameters["@unitCost"].Value   
                                             = orderLineItem.UnitCost;  
            insertProductLineItemCommand.Parameters["@quantity"].Value   
                                             = orderLineItem.Quantity;  
            rowsAffected +=   
            insertProductLineItemCommand.ExecuteNonQuery();  
            }  
            scope.Complete();  
        }  
     }  
     Console.WriteLine(  
     "Updated database with {0} product line items  for purchase order   
                                     {1} ", rowsAffected, po.PONumber);  
    }  
}  
```  
  
 Le comportement du traitement par lots et sa configuration sont spécifiés dans la configuration de l'application de service.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <appSettings>  
    <!-- Use appSetting to configure MSMQ queue name. -->  
    <add key="queueName"   
     value=".\private$\ServiceModelSamplesTransactedBatching" />  
    <add key="baseAddress"   
     value=  
     "http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
    <add key="connectionString" value="Data Source=.\SQLEXPRESS;AttachDbFilename=|DataDirectory|orders.mdf;Integrated Security=True;User Instance=True;" />  
  </appSettings>  
  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ThrottlingBehavior">  
          <serviceThrottling maxConcurrentCalls="5"/>  
        </behavior>  
      </serviceBehaviors>  
  
      <endpointBehaviors>  
        <behavior name="BatchingBehavior">  
          <transactedBatching maxBatchSize="100"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service   
          behaviorConfiguration="ThrottlingBehavior"   
          name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address=  
"net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                  binding="netMsmqBinding"  
                  behaviorConfiguration="BatchingBehavior"   
                  contract=  
                    "Microsoft.ServiceModel.Samples.IOrderProcessor" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  La taille de lot est une indication destinée au système. Par exemple, si vous spécifiez une taille de lot de 20, alors 20 messages seront lus et distribués à l'aide d'une même transaction, puis cette dernière sera validée. Mais il existe des cas où la transaction peut valider le lot avant que la taille de lot soit atteinte.  
>   
>  Un délai d'attente est associé à chaque transaction ; il commence son cycle une fois la transaction créée. Lorsque ce délai d'attente expire la transaction est abandonnée. Ce délai d'attente peut toutefois expirer avant même que la taille de lot soit atteinte. Pour éviter de retraiter le lot à cause de l'abandon, `TransactedBatchingBehavior` vérifie le temps restant sur la transaction. Si 80 % du délai d'attente de transaction sont utilisés, la transaction est validée.  
>   
>  S'il n'y a plus de messages dans la file d'attente, au lieu d'attendre que la taille de lot soit atteinte, la <xref:System.ServiceModel.Description.TransactedBatchingBehavior> valide la transaction.  
>   
>  Le choix de la taille de lot dépend de votre application. Si la taille de lot est trop petite, vous risquez de ne pas obtenir la performance désirée. En revanche, si la taille de lot est trop grande, elle risque de diminuer les performances. Par exemple, la transaction pourrait durer plus longtemps et verrouiller des enregistrements dans votre base de données ou la transaction pourrait se bloquer, ce qui entraînerait la restauration du lot et la nécessité de recommencer le travail.  
  
 Le client crée une étendue de transaction. La communication avec la file d'attente a lieu dans l'étendue de la transaction, entraînant son traitement en tant qu'une unité atomique dans laquelle tous les messages sont envoyés à la file d'attente ou aucun des messages n'est envoyé à la file d'attente. La transaction est validée par l'appel de la méthode <xref:System.Transactions.TransactionScope.Complete%2A> sur l'étendue de la transaction.  
  
```  
//Client implementation code.  
class Client  
{  
    static void Main()  
    {  
        Random randomGen = new Random();  
        for (int i = 0; i < 2500; i++)  
        {  
            // Create a client with given client endpoint configuration.  
            OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
            // Create the purchase order.  
            PurchaseOrder po = new PurchaseOrder();  
            po.CustomerId = "somecustomer" + i + ".com";  
            po.PONumber = Guid.NewGuid().ToString();  
  
            PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
            lineItem1.ProductId = "Blue Widget";  
            lineItem1.Quantity = randomGen.Next(1, 100);  
            lineItem1.UnitCost = (float)randomGen.NextDouble() * 10;  
  
            PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();  
            lineItem2.ProductId = "Red Widget";  
            lineItem2.Quantity = 890;  
            lineItem2.UnitCost = 45.89F;  
  
            po.orderLineItems = new PurchaseOrderLineItem[2];  
            po.orderLineItems[0] = lineItem1;  
            po.orderLineItems[1] = lineItem2;  
  
            //Create a transaction scope.  
            using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
            {  
                // Make a queued call to submit the purchase order.  
                client.SubmitPurchaseOrder(po);  
                // Complete the transaction.  
                scope.Complete();  
            }  
  
            client.Close();  
        }  
        Console.WriteLine();  
        Console.WriteLine("Press <ENTER> to terminate client.");  
        Console.ReadLine();  
    }  
}  
```  
  
 Lorsque vous exécutez l'exemple, les activités du client et du service s'affichent dans leurs fenêtres de console respectives. Vous pouvez voir le service recevoir des messages du client. Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client. Notez qu'en raison de l'utilisation de la mise en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément. Vous pouvez exécuter le client, l'arrêter, puis démarrer le service et il recevra encore ses messages. Vous pouvez voir une sortie en continu à mesure que les messages sont lus dans un lot et traités.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Updated database with 2 product line items for purchase order 493ac832-d216-4e94-b2a5-d7f492fb5e39  
Processing Purchase Order: 8b567f5b-0661-4662-aae2-6cef1bd6d278  
        Customer: somecustomer849.com  
        OrderDetails  
               Order LineItem: 80 of Blue Widget @unit price: $9.751623  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41622.23  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 41130b95-4ea8-40a9-91c3-2e129117fcb8  
Processing Purchase Order: 5ce2699d-9a31-4cc2-a8c5-64cda614b3c7  
        Customer: somecustomer850.com  
        OrderDetails  
               Order LineItem: 89 of Blue Widget @unit price: $6.369128  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41408.95  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 8b567f5b-0661-4662-aae2-6cef1bd6d278  
Processing Purchase Order: ea94486b-7c86-4309-a42d-2f06c00656cd  
        Customer: somecustomer851.com  
        OrderDetails  
             Order LineItem: 47 of Blue Widget @unit price: $0.9391424  
             Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $40886.24  
        Order status: Pending  
```  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Batching`  
  
## <a name="see-also"></a>Voir aussi
