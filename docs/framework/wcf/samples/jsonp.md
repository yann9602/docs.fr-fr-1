---
title: JSONP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02332e04f729abd125f43acdbe0883851004537e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="jsonp"></a>JSONP
Cet exemple montre comment prendre en charge JSON with Padding (JSONP) dans les services WCF REST. JSONP est une convention servant à appeler des scripts entre domaines en générant des balises de script dans le document actif. Le résultat est retourné dans une fonction de rappel spécifiée. JSONP repose sur le principe que les balises telles que \<script src = « http:/ /... » > peuvent évaluer des scripts à partir de n’importe quel domaine, et le script récupéré par ces balises est évalué dans une portée dans laquelle d’autres fonctions peuvent déjà être définies.  
  
## <a name="demonstrates"></a>Démonstrations  
 Script entre domaines avec JSONP.  
  
## <a name="discussion"></a>Discussion  
 L'exemple inclut une page Web qui ajoute dynamiquement un bloc de script après que la page a été rendue dans le navigateur. Ce bloc de script appelle un service WCF REST qui a une seule opération, `GetCustomer`. Le service WCF REST retourne le nom et l'adresse d'un client encapsulés dans un nom de fonction de rappel. Lorsque le service WCF REST répond, la fonction de rappel de la page Web est appelée avec les données client et la fonction de rappel affiche les données dans la page Web. L'injection de la balise de script et l'exécution de la fonction de rappel sont gérées automatiquement par le contrôle ASP.NET AJAX ScriptManager. Le modèle d'utilisation est le même qu'avec tous les proxys ASP.NET AJAX, mais comprend une ligne supplémentaire pour activer JSONP, comme le montre le code suivant :  
  
```csharp  
var proxy = new JsonpAjaxService.CustomerService();  
proxy.set_enableJsonp(true);  
proxy.GetCustomer(onSuccess, onFail, null);  
```  
  
 La page Web peut appeler le service WCF REST, car le service utilise le <xref:System.ServiceModel.Description.WebScriptEndpoint> avec `crossDomainScriptAccessEnabled` ayant la valeur `true`. Ces deux configurations sont effectuent dans le fichier Web.config sous le \<system.serviceModel > élément.  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
  <standardEndpoints>  
    <webScriptEndpoint>  
      <standardEndpoint name="" crossDomainScriptAccessEnabled="true"/>  
    </webScriptEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 ScriptManager gère l'interaction avec le service et cache la complexité de l'implémentation manuelle de l'accès JSONP. Lorsque `crossDomainScriptAccessEnabled` a la valeur `true` et que le format de réponse d'une opération est JSON, l'infrastructure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] recherche dans l'URI de la demande un paramètre de chaîne de requête de rappel et inclut la réponse JSON dans un wrapper avec la valeur du paramètre de chaîne de requête de rappel. Dans l'exemple, la page Web appelle le service WCF REST avec l'URI suivant.  
  
```  
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0  
```  
  
 Étant donné que le paramètre de chaîne de requête de rappel a la valeur `JsonPCallback`, le service WCF retourne une réponse JSONP représentée dans l'exemple suivant.  
  
```  
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});  
```  
  
 Cette réponse JSONP inclut les données client mises au format JSON et encapsulées avec le nom de la fonction de rappel que la page Web a demandée. ScriptManager exécute ce rappel à l'aide d'une balise de script pour effectuer la demande entre domaines, puis passe le résultat au gestionnaire onSuccess qui a été passé à l'opération GetCustomer du proxy ASP.NET AJAX.  
  
 L'exemple se compose de deux applications Web ASP.NET : l'une contient juste un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ; l'autre contient la page Web .aspx qui appelle le service. Lors de l'exécution de la solution, [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] héberge les deux sites Web sur des ports différents, ce qui crée un environnement où le service et le client résident dans des domaines différents.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>Pour exécuter l'exemple  
  
1.  Ouvrez la solution de l'exemple JSONP.  
  
2.  Appuyez sur F5 pour lancer le lien hypertexte « http://localhost:26648/JSONPClientPage.aspx » http://localhost:26648/JSONPClientPage.aspx dans le navigateur.  
  
3.  Notez qu’après le chargement de la page, les entrées de texte pour le « Nom » et « Address » sont remplies par les valeurs.  Ces valeurs ont été fournies à partir d'un appel au service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] alors que le navigateur avait effectué le rendu de la page.
