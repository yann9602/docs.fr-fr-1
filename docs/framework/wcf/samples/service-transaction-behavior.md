---
title: Service Transaction Behavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4c7c9c78b821f7457f193d24bae031d49b301ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="service-transaction-behavior"></a>Service Transaction Behavior
Cet exemple illustre l’utilisation d’une transaction coordonnée par le client et les paramètres de ServiceBehaviorAttribute et OperationBehaviorAttribute pour contrôler le comportement de la transaction du service. Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente un service de calculatrice, mais qui est étendu pour conserver un journal des opérations effectuées dans une table de base de données et un avec état en cours d’exécution total pour les opérations de calcul du serveur. Les écritures rendues persistantes dans la table du journal de serveur dépendent du résultat d’une transaction coordonnée par le client : si la transaction cliente ne se complète pas, la transaction de service Web garantit que les mises à jour de la base de données ne sont pas validées.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Le contrat pour le service définit que toutes les opérations requièrent qu’une transaction soit transmise avec les demandes :  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples",  
                    SessionMode = SessionMode.Required)]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Subtract(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Multiply(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Divide(double n);  
}  
```  
  
 Pour activer le flux de transaction entrant, le service est configuré avec la wsHttpBinding fournie par le système, avec l'attribut transactionFlow ayant la valeur `true`. Cette liaison utilise le protocole WSAtomicTransactionOctober2004 interopérable :  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="transactionalBinding" transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
 Après avoir initialisé à la fois une connexion au service et une transaction, le client accède à plusieurs opérations de service dans l'étendue de cette transaction, puis complète la transaction et ferme la connexion :  
  
```  
// Create a client  
CalculatorClient client = new CalculatorClient();  
  
// Create a transaction scope with the default isolation level of Serializable  
using (TransactionScope tx = new TransactionScope())  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation.  
    double value = 100.00D;  
    Console.WriteLine("  Adding {0}, running total={1}",  
                                        value, client.Add(value));  
  
    // Call the Subtract service operation.  
    value = 45.00D;  
    Console.WriteLine("  Subtracting {0}, running total={1}",  
                                        value, client.Subtract(value));  
  
    // Call the Multiply service operation.  
    value = 9.00D;  
    Console.WriteLine("  Multiplying by {0}, running total={1}",  
                                        value, client.Multiply(value));  
  
    // Call the Divide service operation.  
    value = 15.00D;  
    Console.WriteLine("  Dividing by {0}, running total={1}",  
                                        value, client.Divide(value));  
  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
  
// Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
 Sur le service, il y a trois attributs qui affectent le comportement de la transaction de service, et qui procèdent comme suit :  
  
-   Sur le `ServiceBehaviorAttribute` :  
  
    -   La propriété `TransactionTimeout` spécifie le délai dans lequel une nouvelle transaction doit s'exécuter. Dans cet exemple, elle a pour valeur 30 secondes.  
  
    -   La propriété `TransactionIsolationLevel` spécifie le niveau d'isolation que le service prend en charge. Il doit correspondre au niveau d'isolation du client.  
  
    -   La propriété `ReleaseServiceInstanceOnTransactionComplete` spécifie si l'instance de service sous-jacente est recyclée à la fin de l'exécution d'une transaction. Si elle a la valeur `false`, le service maintient la même instance de service à travers les demandes de l'opération. Cela est nécessaire pour maintenir le total évolutif. Si elle a la valeur `true`, une nouvelle instance est générée après chaque action complétée.  
  
    -   La propriété `TransactionAutoCompleteOnSessionClose` spécifie si les transactions en attente sont exécutées lorsque la session se ferme. En lui affectant `false`, les opérations individuelles doivent affecter la `OperationBehaviorAttribute``TransactionAutoComplete` propriété `true` ou requérir explicitement un appel à la `SetTransactionComplete` méthode pour exécuter des transactions. Cet exemple illustre les deux approches.  
  
-   Sur le `ServiceContractAttribute` :  
  
    -   La propriété `SessionMode` spécifie si le service met en corrélation les demandes appropriées dans une session logique. Étant donné que ce service inclut des opérations où la propriété OperationBehaviorAttribute TransactionAutoComplete a la valeur `false` (multiplication et division), `SessionMode.Required` doit être spécifié. Par exemple, l'opération de multiplication n'exécute pas sa transaction et à la place compte sur un appel ultérieur à l'opération de division pour s'exécuter à l'aide de la méthode `SetTransactionComplete` ; le service doit être en mesure de déterminer que ces opérations se produisent dans la même session.  
  
-   Sur le `OperationBehaviorAttribute` :  
  
    -   La propriété `TransactionScopeRequired` spécifie si les actions de l'opération doivent être exécutées dans une étendue de transaction. Elle a la valeur `true` pour toutes les opérations dans cet exemple et, vu que le client transmet sa transaction à toutes les opérations, les actions se produisent dans l'étendue de cette transaction cliente.  
  
    -   La propriété `TransactionAutoComplete` spécifie si la transaction dans laquelle la méthode s'exécute est automatiquement effectuée si aucune exception non prise en charge n'est levée. Comme décrit précédemment, cette propriété a la valeur `true` pour les opérations d'addition et de soustraction mais `false` pour les opérations de multiplication et de division. Les opérations d'addition et de soustraction s'exécutent automatiquement, l'opération de division s'exécute à travers un appel explicite à la méthode `SetTransactionComplete`, et l'opération de multiplication ne s'exécute mais à la place compte sur un appel ultérieur obligatoire, à l'opération de division par exemple, pour s'exécuter.  
  
 L'implémentation du service doté d'attributs se déroule comme suit :  
  
```  
[ServiceBehavior(  
    TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
    TransactionTimeout = "00:00:30",  
    ReleaseServiceInstanceOnTransactionComplete = false,  
    TransactionAutoCompleteOnSessionClose = false)]  
public class CalculatorService : ICalculator  
{  
    double runningTotal;  
  
    public CalculatorService()  
    {  
        Console.WriteLine("Creating new service instance...");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public double Add(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n, runningTotal));  
        runningTotal = runningTotal + n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public double Subtract(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n, runningTotal));  
        runningTotal = runningTotal - n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]  
    public double Multiply(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", runningTotal, n));  
        runningTotal = runningTotal * n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]  
    public double Divide(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", runningTotal, n));  
        runningTotal = runningTotal / n;  
        OperationContext.Current.SetTransactionComplete();  
        return runningTotal;  
    }  
  
    // Logging method ommitted for brevity  
}   
```  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
```  
Starting transaction  
Performing calculations...  
  Adding 100, running total=100  
  Subtracting 45, running total=55  
  Multiplying by 9, running total=495  
  Dividing by 15, running total=33  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 Le journal des demandes faites à l'opération de service est visible dans la fenêtre de console du service. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
```  
Press <ENTER> to terminate service.  
Creating new service instance...  
  Writing row 1 to database: Adding 100 to 0  
  Writing row 2 to database: Subtracting 45 from 100  
  Writing row 3 to database: Multiplying 55 by 9  
  Writing row 4 to database: Dividing 495 by 15  
```  
  
 Notez qu'en plus de conserver le total évolutif des calculs, le service signale la création d'instances (une instance pour cet exemple) et enregistre les demandes d'opération dans une base de données. Étant donné que toutes les demandes transmettent la transaction du client, tout échec d’exécution de cette transaction entraîne la restauration de toutes les opérations de la base de données. Cela peut être démontré de plusieurs manières :  
  
-   Supprimez l'appel du client à `tx.Complete` () et répétez la transaction : le client quitte l'étendue de la transaction sans l'exécuter.  
  
-   Supprimez l’appel à l’opération de division du service : cela empêche l’action initiée par l’opération de multiplication de s’effectuer. Par conséquent, la transaction du client échoue également.  
  
-   Levez une exception non gérée n'importe où dans l'étendue de transaction du client : cela empêche également le client d'exécuter sa transaction.  
  
 Le résultat est toujours le même : aucune des opérations exécutées dans cette étendue n'est validée et le nombre de lignes rendues persistantes dans la base de données n'est pas incrémenté.  
  
> [!NOTE]
>  Dans le cadre du processus de génération, le fichier de la base de données est copié dans le dossier bin. Vous devez examiner cette copie du fichier de la base de données pour observer les lignes rendues persistantes dans le journal plutôt que dans le fichier inclus dans le projet Visual Studio.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Vérifiez que vous avez installé SQL Server 2005 Express Edition ou SQL Server 2005. Dans le fichier App.config du service, le `connectionString` de la base de données peut être défini ou les interactions avec la base de données peuvent être désactivées en affectant `usingSql` à la valeur `false` d'appSettings.  
  
2.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Si vous exécutez l'exemple sur plusieurs ordinateurs, vous devez configurer le Microsoft Distributed Transaction Coordinator (MSDTC) pour activer le flux de transaction réseau et utiliser l'outil WsatConfig.exe pour activer la gestion réseau des transactions [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a>Pour configurer le Microsoft Distributed Transaction Coordinator (MSDTC) de manière à prendre en charge l’exécution de l’exemple sur plusieurs ordinateurs  
  
1.  Sur l’ordinateur de service, configurez MSDTC pour autoriser des transactions réseau entrantes.  
  
    1.  À partir de la **Démarrer** menu, accédez à **le panneau de configuration**, puis **outils d’administration**, puis **Services de composants**.  
  
    2.  Avec le bouton droit **poste** et sélectionnez **propriétés**.  
  
    3.  Sur le **MSDTC** , cliquez sur **Configuration de la sécurité**.  
  
    4.  Vérifiez **les accès DTC réseau** et **autoriser entrant**.  
  
    5.  Cliquez sur **Oui** à redémarrer le service MS DTC, puis cliquez sur **OK**.  
  
    6.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
2.  Sur l’ordinateur du service et l’ordinateur du client, configurez le Pare-feu Windows pour inclure le Microsoft Distributed Transaction Coordinator (MSDTC) à la liste des exceptions :  
  
    1.  Exécutez l’application de Pare-feu Windows à partir du Panneau de configuration.  
  
    2.  À partir de la **Exceptions** , cliquez sur **ajouter un programme**.  
  
    3.  Naviguez jusqu’au dossier C:\WINDOWS\System32.  
  
    4.  Sélectionnez Msdtc.exe et cliquez sur **ouvrir**.  
  
    5.  Cliquez sur **OK** pour fermer la **ajouter un programme** boîte de dialogue, puis cliquez sur **OK** à nouveau pour fermer l’applet de pare-feu Windows.  
  
3.  Sur l’ordinateur client, configurez MSDTC pour autoriser les transactions réseau sortantes :  
  
    1.  À partir de la **Démarrer** menu, accédez à **le panneau de configuration**, puis **outils d’administration**, puis **Services de composants**.  
  
    2.  Avec le bouton droit **poste** et sélectionnez **propriétés**.  
  
    3.  Sur le **MSDTC** , cliquez sur **Configuration de la sécurité**.  
  
    4.  Vérifiez **les accès DTC réseau** et **autoriser les transactions sortantes**.  
  
    5.  Cliquez sur **Oui** à redémarrer le service MS DTC, puis cliquez sur **OK**.  
  
    6.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`  
  
## <a name="see-also"></a>Voir aussi
