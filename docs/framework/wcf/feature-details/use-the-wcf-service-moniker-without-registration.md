---
title: "Comment : utiliser le moniker de service Windows Communication Foundation sans inscription"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7e859f0eddf93191a01230508742c0777ec73751
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a><span data-ttu-id="27681-102">Comment : utiliser le moniker de service Windows Communication Foundation sans inscription</span><span class="sxs-lookup"><span data-stu-id="27681-102">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>
<span data-ttu-id="27681-103">Pour se connecter à un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et communiquer avec ce dernier, une application cliente [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] doit être en possession des détails de l'adresse du service, de la configuration de liaison et du contrat de service.</span><span class="sxs-lookup"><span data-stu-id="27681-103">To connect to and communicate with a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application must have the details of the service address, the binding configuration, and the service contract.</span></span>  
  
 <span data-ttu-id="27681-104">Le moniker de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obtient généralement le contrat requis par le biais de l'inscription préalable des types d'attributs requis, mais cela n'est pas toujours possible.</span><span class="sxs-lookup"><span data-stu-id="27681-104">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker typically obtains the required contract through prior registration of the required attribute types, but there might be cases where this is not feasible.</span></span> <span data-ttu-id="27681-105">À la place de l'inscription, le moniker peut obtenir la définition du contrat sous la forme d'un document WSDL (Web Services Definition Language) en utilisant le paramètre `wsdl` ou par le biais de l'échange de métadonnées en utilisant le paramètre `mexAddress`.</span><span class="sxs-lookup"><span data-stu-id="27681-105">In place of registration, the moniker can obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document, through the use of the `wsdl` parameter or through Metadata Exchange, through the use of the `mexAddress` parameter.</span></span>  
  
 <span data-ttu-id="27681-106">Cela permet de prendre en charge des scénarios comme la distribution d'une feuille de calcul Excel dans laquelle certaines valeurs de cellules sont calculées par le biais d'interactions de services Web.</span><span class="sxs-lookup"><span data-stu-id="27681-106">This enables scenarios such as the distribution of an Excel spreadsheet where some of the cell values are calculated through Web service interactions.</span></span> <span data-ttu-id="27681-107">Dans ce scénario, il peut ne pas être possible d'inscrire l'assembly de contrat de service sur tous les clients susceptibles d'ouvrir le document.</span><span class="sxs-lookup"><span data-stu-id="27681-107">In this scenario, it might not be feasible to register the service contract assembly on all clients that might open the document.</span></span> <span data-ttu-id="27681-108">Les paramètres `wsdl` et `mexAddress` offrent une solution autonome.</span><span class="sxs-lookup"><span data-stu-id="27681-108">The `wsdl` parameter or the `mexAddress` parameter enables a self-contained solution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27681-109">L'authentification mutuelle doit être utilisée pour la protection contre la falsification ou l'usurpation de demandes et de réponses.</span><span class="sxs-lookup"><span data-stu-id="27681-109">Mutual authentication must be used to protect against request and response tampering or spoofing.</span></span> <span data-ttu-id="27681-110">Il est en particulier important pour les clients d'avoir la garantie que le point de terminaison d'échange de métadonnées qui répond est le tiers de confiance attendu.</span><span class="sxs-lookup"><span data-stu-id="27681-110">Specifically, it is important for clients to be assured that the Metadata Exchange endpoint that is responding is the intended trusted party.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27681-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="27681-111">Example</span></span>  
 <span data-ttu-id="27681-112">Cet exemple montre l'utilisation du moniker de service avec un contrat MEX.</span><span class="sxs-lookup"><span data-stu-id="27681-112">This example shows the use of the service moniker with a MEX contract.</span></span> <span data-ttu-id="27681-113">Un service associé au contrat suivant est exposé avec un wsHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="27681-113">A service with the following contract is exposed with a wsHttpBinding.</span></span>  
  
```  
using System.ServiceModel;  
  
...  
  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Demo")]  
public interface IAffiliate  
{  
    [OperationContract]  
    bool NewAffiliate(string ID, string company, string fullname, string accountsCode);  
    [OperationContract]  
    bool RemoveAffiliate(string ID);  
    [OperationContract]  
    double RevenueCheckMonthly(ref string ID);  
    [OperationContract]  
    double RevenueCheckTotal(ref string ID);  
}  
```  
  
 <span data-ttu-id="27681-114">Pour construire un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour le service distant, l'exemple de chaîne de moniker suivant peut être utilisé :</span><span class="sxs-lookup"><span data-stu-id="27681-114">To construct a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client for the remote service the following example moniker string can be used.</span></span>  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 <span data-ttu-id="27681-115">Pendant l'exécution de l'application cliente, le client exécute un `WS-MetadataExchange` avec le paramètre `mexAddress`.</span><span class="sxs-lookup"><span data-stu-id="27681-115">During the execution of the client application, the client performs a `WS-MetadataExchange` with the provided `mexAddress`.</span></span> <span data-ttu-id="27681-116">Les détails de l'adresse, de la liaison et du contrat peuvent alors être retournés pour un certains nombre de services.</span><span class="sxs-lookup"><span data-stu-id="27681-116">This might return the address, binding and contract details for a number of services.</span></span> <span data-ttu-id="27681-117">Les paramètres `address`, `contract`, `contractNamespace`, `binding` et `bindingNamespace` sont utilisés pour identifier le service concerné.</span><span class="sxs-lookup"><span data-stu-id="27681-117">The `address`, `contract`, `contractNamespace`, `binding` and `bindingNamespace` parameters are used to identify the intended service.</span></span> <span data-ttu-id="27681-118">Une fois ces paramètres mis en correspondance, le moniker construit un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec la définition de contrat appropriée, puis des appels peuvent être effectués à l'aide du client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], comme avec le contrat typé.</span><span class="sxs-lookup"><span data-stu-id="27681-118">Once those parameters have been matched, the moniker constructs a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client with the appropriate contract definition and calls can then be made using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, as with the typed contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27681-119">Si le moniker est incorrect ou si le service n'est pas disponible, l'appel à `GetObject` retourne une erreur indiquant que la syntaxe n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="27681-119">If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error saying "Invalid Syntax".</span></span> <span data-ttu-id="27681-120">Si vous recevez cette erreur, assurez-vous que le moniker que vous utilisez est correct et que le service est disponible.</span><span class="sxs-lookup"><span data-stu-id="27681-120">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27681-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27681-121">See Also</span></span>  
 [<span data-ttu-id="27681-122">Comment : inscrire et configurer un Moniker de Service</span><span class="sxs-lookup"><span data-stu-id="27681-122">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
