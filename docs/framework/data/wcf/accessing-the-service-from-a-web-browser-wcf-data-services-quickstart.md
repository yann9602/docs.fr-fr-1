---
title: "Accès au service à partir d'un navigateur Web (démarrage rapide des services de données WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71beb254bf258da97207f14afca73cd68c6927ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a><span data-ttu-id="599a9-102">Accès au service à partir d'un navigateur Web (démarrage rapide des services de données WCF)</span><span class="sxs-lookup"><span data-stu-id="599a9-102">Accessing the Service from a Web Browser (WCF Data Services Quickstart)</span></span>
<span data-ttu-id="599a9-103">Dans cette tâche, vous allez démarrer [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] à partir de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] et éventuellement désactiver la lecture de flux dans le navigateur Web.</span><span class="sxs-lookup"><span data-stu-id="599a9-103">In this task, you will start the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] from [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] and optionally disable feed reading in the Web browser.</span></span> <span data-ttu-id="599a9-104">Vous serez ensuite extraire le document de définition de service ainsi accéder aux ressources du service de données en soumettant des demandes HTTP GET via un navigateur Web aux ressources exposées.</span><span class="sxs-lookup"><span data-stu-id="599a9-104">You will then retrieve the service definition document as well as access data service resources by submitting HTTP GET requests through a Web browser to the exposed resources.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="599a9-105">Par défaut, [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] affecte automatiquement un numéro de port à l'URI `localhost` sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="599a9-105">By default, [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] auto-assigns a port number to the `localhost` URI on your computer.</span></span> <span data-ttu-id="599a9-106">Cette tâche utilise le numéro de port `12345` dans les exemples d'URI.</span><span class="sxs-lookup"><span data-stu-id="599a9-106">This task uses the port number `12345` in the URI examples.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="599a9-107">comment définir un numéro de port spécifique dans votre [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] projet consultez [création du Service de données](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="599a9-107"> how to set a specific port number in your [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] project see [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>  
  
### <a name="to-request-the-default-service-document-by-using-internet-explorer"></a><span data-ttu-id="599a9-108">Pour demander le document de service par défaut à l'aide d'Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="599a9-108">To request the default service document by using Internet Explorer</span></span>  
  
1.  <span data-ttu-id="599a9-109">Dans Internet Explorer, à partir de la **outils** menu, sélectionnez **Options Internet**, cliquez sur le **contenu** , cliquez sur **paramètres**et désactivez  **Activer la lecture du flux**.</span><span class="sxs-lookup"><span data-stu-id="599a9-109">In Internet Explorer, from the **Tools** menu, select **Internet Options**, click the **Content** tab, click **Settings**, and clear **Turn on feed viewing**.</span></span>  
  
     <span data-ttu-id="599a9-110">Cette opération garantit que la lecture de flux est désactivée.</span><span class="sxs-lookup"><span data-stu-id="599a9-110">This makes sure that feed reading is disabled.</span></span> <span data-ttu-id="599a9-111">Si vous ne désactivez pas cette fonctionnalité, le navigateur Web traitera le document encodé AtomPub retourné comme un flux XML au lieu d'afficher les données XML brutes.</span><span class="sxs-lookup"><span data-stu-id="599a9-111">If you do not disable this functionality, then the Web browser will treat the returned AtomPub encoded document as an XML feed instead of displaying the raw XML data.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="599a9-112">Si votre navigateur ne peut pas afficher le flux sous forme de données XML brutes, vous devriez encore être en mesure de voir le flux sous forme de code source de la page.</span><span class="sxs-lookup"><span data-stu-id="599a9-112">If your browser cannot display the feed as raw XML data, you should still be able to view the feed as the source code for the page.</span></span>  
  
2.  <span data-ttu-id="599a9-113">Dans [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], appuyez sur la touche F5 pour démarrer le débogage de l'application.</span><span class="sxs-lookup"><span data-stu-id="599a9-113">In [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], press the F5 key to start debugging the application.</span></span>  
  
3.  <span data-ttu-id="599a9-114">Ouvrez un navigateur Web sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="599a9-114">Open a Web browser on the local computer.</span></span> <span data-ttu-id="599a9-115">Dans la barre d'adresses, entrez l'URI suivant :</span><span class="sxs-lookup"><span data-stu-id="599a9-115">In the address bar, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc  
    ```  
  
     <span data-ttu-id="599a9-116">Cette opération retourne le document du service par défaut qui contient une liste des jeux d'entités exposés par ce service de données.</span><span class="sxs-lookup"><span data-stu-id="599a9-116">This returns the default service document, which contains a list of entity sets that are exposed by this data service.</span></span>  
  
### <a name="to-access-entity-set-resources-from-a-web-browser"></a><span data-ttu-id="599a9-117">Pour accéder aux ressources de jeu d'entités depuis un navigateur Web</span><span class="sxs-lookup"><span data-stu-id="599a9-117">To access entity set resources from a Web browser</span></span>  
  
1.  <span data-ttu-id="599a9-118">Dans la barre d'adresse de votre navigateur Web, entrez l'URI suivant :</span><span class="sxs-lookup"><span data-stu-id="599a9-118">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers  
    ```  
  
     <span data-ttu-id="599a9-119">Cette opération retourne un jeu de tous les clients dans l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="599a9-119">This returns a set of all customers in the Northwind sample database.</span></span>  
  
2.  <span data-ttu-id="599a9-120">Dans la barre d'adresse de votre navigateur Web, entrez l'URI suivant :</span><span class="sxs-lookup"><span data-stu-id="599a9-120">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')  
    ```  
  
     <span data-ttu-id="599a9-121">Cette opération retourne une instance d'entité pour le client spécifique, `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="599a9-121">This returns an entity instance for the specific customer, `ALFKI`.</span></span>  
  
3.  <span data-ttu-id="599a9-122">Dans la barre d'adresse de votre navigateur Web, entrez l'URI suivant :</span><span class="sxs-lookup"><span data-stu-id="599a9-122">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders  
    ```  
  
     <span data-ttu-id="599a9-123">Cette opération parcourt la relation entre les clients et les ordres pour retourner un jeu de tous les ordres pour le client `ALFKI` spécifique.</span><span class="sxs-lookup"><span data-stu-id="599a9-123">This traverses the relationship between customers and orders to return a set of all orders for the specific customer `ALFKI`.</span></span>  
  
4.  <span data-ttu-id="599a9-124">Dans la barre d'adresse de votre navigateur Web, entrez l'URI suivant :</span><span class="sxs-lookup"><span data-stu-id="599a9-124">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643  
    ```  
  
     <span data-ttu-id="599a9-125">Cette opération filtre des ordres qui appartiennent au client `ALFKI` spécifique afin que seul un ordre spécifique soit retourné selon la valeur `OrderID` fournie.</span><span class="sxs-lookup"><span data-stu-id="599a9-125">This filters orders that belong to the specific customer `ALFKI` so that only a specific order is returned based on the supplied `OrderID` value.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="599a9-126">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="599a9-126">Next Steps</span></span>  
 <span data-ttu-id="599a9-127">Vous avez correctement accédé à [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] depuis un navigateur Web, et le navigateur a émis des demandes HTTP GET aux ressources spécifiées.</span><span class="sxs-lookup"><span data-stu-id="599a9-127">You have successfully accessed the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] from a Web browser, with the browser issuing HTTP GET requests to specified resources.</span></span> <span data-ttu-id="599a9-128">Un navigateur Web fournit un moyen simple d'expérimenter la syntaxe d'adressage des demandes et d'afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="599a9-128">A Web browser provides an easy way to experiment with the addressing syntax of requests and view the results.</span></span> <span data-ttu-id="599a9-129">Toutefois, un service des données de production n'est pas accessible en général par cette méthode.</span><span class="sxs-lookup"><span data-stu-id="599a9-129">However, a production data service is not generally accessed by this method.</span></span> <span data-ttu-id="599a9-130">Généralement, les applications interagissent avec le service de données par le biais de code d'application ou de langages de script.</span><span class="sxs-lookup"><span data-stu-id="599a9-130">Typically, applications interact with the data service through application code or scripting languages.</span></span> <span data-ttu-id="599a9-131">Ensuite, vous allez créer une application cliente qui utilise des bibliothèques clientes pour accéder aux ressources du service des données comme s'il s'agissait d'objets CLR (Common Language runtime) :</span><span class="sxs-lookup"><span data-stu-id="599a9-131">Next, you will create a client application that uses client libraries to access data service resources as if they were common language runtime (CLR) objects:</span></span>  
  
 [<span data-ttu-id="599a9-132">Création de l’application cliente du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="599a9-132">Creating the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a><span data-ttu-id="599a9-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="599a9-133">See Also</span></span>  
 [<span data-ttu-id="599a9-134">Accès aux ressources d’un service de données</span><span class="sxs-lookup"><span data-stu-id="599a9-134">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
