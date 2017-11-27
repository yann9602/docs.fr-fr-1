---
title: "Compléments et extensibilité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extensibility [.NET Framework], add-ins
- add-ins [.NET Framework]
- add-ins [.NET Framework], about
- hosts [.NET Framework], compared to add-ins
- .NET Framework, add-ins
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], compared to hosts
- .NET Framework, extensibility
- versioning [.NET Framework], add-ins
ms.assetid: 8dd45b02-7218-40f9-857d-40d7b98b850b
caps.latest.revision: "42"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9bd09d0da70869ba193b414d8a2ce6c25cbb6b38
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2017
---
# <a name="add-ins-and-extensibility"></a><span data-ttu-id="960b1-102">Compléments et extensibilité</span><span class="sxs-lookup"><span data-stu-id="960b1-102">Add-ins and Extensibility</span></span>
<span data-ttu-id="960b1-103"><a name="top"></a> Les compléments fournissent des fonctionnalités ou des services étendus pour une application hôte.</span><span class="sxs-lookup"><span data-stu-id="960b1-103"><a name="top"></a> Add-ins provide extended features or services for a host application.</span></span> <span data-ttu-id="960b1-104">Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] fournit un modèle de programmation que les développeurs peuvent utiliser pour développer des compléments et les activer dans leur application hôte.</span><span class="sxs-lookup"><span data-stu-id="960b1-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides a programming model that developers can use to develop add-ins and activate them in their host application.</span></span> <span data-ttu-id="960b1-105">Le modèle permet de réaliser ceci en construisant un pipeline de communication entre l'hôte et le complément.</span><span class="sxs-lookup"><span data-stu-id="960b1-105">The model achieves this by constructing a communication pipeline between the host and the add-in.</span></span> <span data-ttu-id="960b1-106">Le modèle est implémenté à l'aide des types des espaces de noms <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>et <xref:System.AddIn.Contract> .</span><span class="sxs-lookup"><span data-stu-id="960b1-106">The model is implemented by using the types in the <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, and <xref:System.AddIn.Contract> namespaces.</span></span>  
  
 <span data-ttu-id="960b1-107">Cette vue d'ensemble contient les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="960b1-107">This overview contains the following sections:</span></span>  
  
-   [<span data-ttu-id="960b1-108">Modèle de complément</span><span class="sxs-lookup"><span data-stu-id="960b1-108">Add-in Model</span></span>](#addin_model)  
  
-   [<span data-ttu-id="960b1-109">Distinction entre les hôtes et les compléments</span><span class="sxs-lookup"><span data-stu-id="960b1-109">Distinguishing Between Add-ins and Hosts</span></span>](#distinguishing_between_addins_and_hosts)  
  
-   [<span data-ttu-id="960b1-110">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="960b1-110">Related Topics</span></span>](#related_topics)  
  
-   [<span data-ttu-id="960b1-111">Référence</span><span class="sxs-lookup"><span data-stu-id="960b1-111">Reference</span></span>](#reference)  
  
> [!NOTE]
>  <span data-ttu-id="960b1-112">Vous trouverez des exemples de code supplémentaires et des aperçus des technologies des clients traitant des outils pour créer des pipelines de compléments sur le [site de l’extensibilité et des compléments gérés de Framework sur CodePlex](http://go.microsoft.com/fwlink/?LinkId=121190).</span><span class="sxs-lookup"><span data-stu-id="960b1-112">You can find additional sample code, and customer technology previews of tools for building add-in pipelines, at the [Managed Extensibility and Add-In Framework site on CodePlex](http://go.microsoft.com/fwlink/?LinkId=121190).</span></span>  
  
<a name="addin_model"></a>   
## <a name="add-in-model"></a><span data-ttu-id="960b1-113">Modèle de complément</span><span class="sxs-lookup"><span data-stu-id="960b1-113">Add-in Model</span></span>  
 <span data-ttu-id="960b1-114">Le modèle de complément se compose d'une série de segments qui constituent le pipeline de complément (également appelé pipeline de communication), qui est responsable de toutes les communications entre le complément et l'hôte.</span><span class="sxs-lookup"><span data-stu-id="960b1-114">The add-in model consists of a series of segments that make up the add-in pipeline (also known as the communication pipeline), that is responsible for all communication between the add-in and the host.</span></span> <span data-ttu-id="960b1-115">Le pipeline est un modèle de communication symétrique de segments qui échangent des données entre un complément et son hôte.</span><span class="sxs-lookup"><span data-stu-id="960b1-115">The pipeline is a symmetrical communication model of segments that exchange data between an add-in and its host.</span></span> <span data-ttu-id="960b1-116">Le développement de ces segments entre l'hôte et le complément fournit les couches d'abstraction requises qui prennent en charge le contrôle de version et l'isolation du complément.</span><span class="sxs-lookup"><span data-stu-id="960b1-116">Developing these segments between the host and the add-in provides the required layers of abstraction that support versioning and isolation of the add-in.</span></span>  
  
 <span data-ttu-id="960b1-117">L'illustration suivante présente le pipeline.</span><span class="sxs-lookup"><span data-stu-id="960b1-117">The following illustration shows the pipeline.</span></span>  
  
 <span data-ttu-id="960b1-118">![Ajouter &#45; dans le modèle de pipeline. ] (../../../docs/framework/add-ins/media/addin1.png "AddIn1")</span><span class="sxs-lookup"><span data-stu-id="960b1-118">![Add&#45;in pipeline model.](../../../docs/framework/add-ins/media/addin1.png "AddIn1")</span></span>  
<span data-ttu-id="960b1-119">Pipeline de complément</span><span class="sxs-lookup"><span data-stu-id="960b1-119">Add-in pipeline</span></span>  
  
 <span data-ttu-id="960b1-120">Les assemblys pour ces segments ne doivent pas obligatoirement se trouver dans le même domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="960b1-120">The assemblies for these segments are not required to be in the same application domain.</span></span> <span data-ttu-id="960b1-121">Vous pouvez charger un complément dans son propre nouveau domaine d'application, dans un domaine d'application existant ou même dans le domaine d'application de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="960b1-121">You can load an add-in into its own new application domain, into an existing application domain, or even into the host's application domain.</span></span> <span data-ttu-id="960b1-122">Vous pouvez charger plusieurs compléments dans le même domaine d'application, ce qui permet aux compléments de partager des ressources et des contextes de sécurité.</span><span class="sxs-lookup"><span data-stu-id="960b1-122">You can load multiple add-ins into the same application domain, which enables the add-ins to share resources and security contexts.</span></span>  
  
 <span data-ttu-id="960b1-123">Le modèle de complément prend en charge et recommande une frontière facultative entre l'hôte et le complément, qui est appelée la frontière d'isolement (également appelée la frontière de mise à distance).</span><span class="sxs-lookup"><span data-stu-id="960b1-123">The add-in model supports, and recommends, an optional boundary between the host and the add-in, which is called the isolation boundary (also known as a remoting boundary).</span></span> <span data-ttu-id="960b1-124">Cette frontière peut être une frontière de domaine d'application ou de processus.</span><span class="sxs-lookup"><span data-stu-id="960b1-124">This boundary can be an application domain or process boundary.</span></span>  
  
 <span data-ttu-id="960b1-125">Le segment de contrat au milieu du pipeline est chargé à la fois dans le domaine d'application de l'hôte et dans le domaine d'application du complément.</span><span class="sxs-lookup"><span data-stu-id="960b1-125">The contract segment in the middle of the pipeline is loaded into both the host's application domain and the add-in's application domain.</span></span> <span data-ttu-id="960b1-126">Le contrat définit les méthodes virtuelles que l'hôte et le complément utilisent pour échanger des types entre eux.</span><span class="sxs-lookup"><span data-stu-id="960b1-126">The contract defines the virtual methods that the host and the add-in use to exchange types with each other.</span></span>  
  
 <span data-ttu-id="960b1-127">Pour passer à travers la frontière d'isolement, les types doivent être des contrats ou des types sérialisables.</span><span class="sxs-lookup"><span data-stu-id="960b1-127">To pass through the isolation boundary, types must be either contracts or serializable types.</span></span> <span data-ttu-id="960b1-128">Les types qui ne sont pas des contrats ou des types sérialisables doivent être convertis en contrats par les segments de l'adaptateur dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="960b1-128">Types that are not contracts or serializable types must be converted to contracts by the adapter segments in the pipeline.</span></span>  
  
 <span data-ttu-id="960b1-129">Les segments de vue du pipeline sont des classes de base abstraites ou des interfaces qui fournissent à l'hôte et au complément une vue des méthodes qu'ils partagent, comme défini par le contrat.</span><span class="sxs-lookup"><span data-stu-id="960b1-129">The view segments of the pipeline are abstract base classes or interfaces that provide the host and the add-in with a view of the methods that they share, as defined by the contract.</span></span>  
  
 <span data-ttu-id="960b1-130">Pour plus d’informations sur le développement de segments de pipeline, consultez [Pipeline Development](../../../docs/framework/add-ins/pipeline-development.md).</span><span class="sxs-lookup"><span data-stu-id="960b1-130">For more information about developing pipeline segments, see [Pipeline Development](../../../docs/framework/add-ins/pipeline-development.md).</span></span>  
  
 <span data-ttu-id="960b1-131">Les sections qui suivent décrivent les fonctionnalités du modèle de complément.</span><span class="sxs-lookup"><span data-stu-id="960b1-131">The sections that follow describe the features of the add-in model.</span></span>  
  
### <a name="independent-versioning"></a><span data-ttu-id="960b1-132">Contrôle de version indépendant</span><span class="sxs-lookup"><span data-stu-id="960b1-132">Independent Versioning</span></span>  
 <span data-ttu-id="960b1-133">Le modèle de complément permet une gestion des versions indépendantes pour les hôtes et pour les compléments.</span><span class="sxs-lookup"><span data-stu-id="960b1-133">The add-in model allows hosts and add-ins to version independently.</span></span> <span data-ttu-id="960b1-134">Le modèle de complément permet donc les scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="960b1-134">As a result, the add-in model enables the following scenarios:</span></span>  
  
-   <span data-ttu-id="960b1-135">Création d'un adaptateur qui permet à un hôte d'utiliser un complément créé pour une version antérieure de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="960b1-135">Creating an adapter that enables a host to use an add-in built for a previous version of the host.</span></span>  
  
-   <span data-ttu-id="960b1-136">Création d'un adaptateur qui permet à un hôte d'utiliser un complément créé pour une version ultérieure de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="960b1-136">Creating an adapter that enables a host to use an add-in built for a later version of the host.</span></span>  
  
-   <span data-ttu-id="960b1-137">Création d'un adaptateur qui permet à un hôte d'utiliser des compléments créés pour un autre hôte.</span><span class="sxs-lookup"><span data-stu-id="960b1-137">Creating an adapter that enables a host to use add-ins built for a different host.</span></span>  
  
### <a name="discovery-and-activation"></a><span data-ttu-id="960b1-138">Découverte et activation</span><span class="sxs-lookup"><span data-stu-id="960b1-138">Discovery and Activation</span></span>  
 <span data-ttu-id="960b1-139">Vous pouvez activer un complément en utilisant un jeton d'une collection qui représente les compléments localisés dans une banque d'informations.</span><span class="sxs-lookup"><span data-stu-id="960b1-139">You can activate an add-in by using a token from a collection that represents the add-ins found from an information store.</span></span> <span data-ttu-id="960b1-140">Les compléments sont trouvés en recherchant le type qui définit la vue du complément de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="960b1-140">Add-ins are found by searching for the type that defines the host's view of the add-in.</span></span> <span data-ttu-id="960b1-141">Vous pouvez aussi trouver un complément spécifique via le type qui définit le complément.</span><span class="sxs-lookup"><span data-stu-id="960b1-141">You can also find a specific add-in by the type that defines the add-in.</span></span> <span data-ttu-id="960b1-142">La banque d'informations se compose de deux fichiers cache : le magasin de pipelines et le magasin de compléments.</span><span class="sxs-lookup"><span data-stu-id="960b1-142">The information store consists of two cache files: the pipeline store and the add-in store.</span></span>  
  
 <span data-ttu-id="960b1-143">Pour plus d'informations sur la mise à jour et la régénération de la banque d'informations, consultez [Découverte des compléments](http://msdn.microsoft.com/en-us/5d268dde-11df-4c4d-a022-f58d88bbc421).</span><span class="sxs-lookup"><span data-stu-id="960b1-143">For information about updating and rebuilding the information store, see [Add-in Discovery](http://msdn.microsoft.com/en-us/5d268dde-11df-4c4d-a022-f58d88bbc421).</span></span> <span data-ttu-id="960b1-144">Pour plus d’informations sur l’activation des compléments, consultez [Activation des compléments](http://msdn.microsoft.com/en-us/bedcbcdf-5964-4215-b5f3-3299798b2b3f) et [Comment : activer des compléments avec différents niveaux d’isolement et de sécurité](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span><span class="sxs-lookup"><span data-stu-id="960b1-144">For information about activating add-ins, see [Add-in Activation](http://msdn.microsoft.com/en-us/bedcbcdf-5964-4215-b5f3-3299798b2b3f) and [How to: Activate Add-ins with Different Isolation and Security](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span></span>  
  
### <a name="isolation-levels-and-external-processes"></a><span data-ttu-id="960b1-145">Niveaux d'isolement et processus externes</span><span class="sxs-lookup"><span data-stu-id="960b1-145">Isolation Levels and External Processes</span></span>  
 <span data-ttu-id="960b1-146">Le modèle de complément prend en charge plusieurs niveaux d'isolement entre un complément et son hôte, ou entre compléments. En commençant par le moins isolé, ces niveaux sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="960b1-146">The add-in model supports several levels of isolation between an add-in and its host or between add-ins. Starting from the least isolated, these levels are as follows:</span></span>  
  
-   <span data-ttu-id="960b1-147">Le complément s'exécute dans le même domaine d'application que l'hôte.</span><span class="sxs-lookup"><span data-stu-id="960b1-147">The add-in runs in the same application domain as the host.</span></span> <span data-ttu-id="960b1-148">Ceci n'est pas recommandé, car vous perdez l'isolement et les capacités de déchargement que vous obtenez quand vous utilisez différents domaines d'application.</span><span class="sxs-lookup"><span data-stu-id="960b1-148">This is not recommended because you lose the isolation and unloading capabilities that you get when you use different application domains.</span></span>  
  
-   <span data-ttu-id="960b1-149">Plusieurs compléments sont chargés dans le même domaine d'application, qui est différent du domaine d'application utilisé par l'hôte.</span><span class="sxs-lookup"><span data-stu-id="960b1-149">Multiple add-ins are loaded into the same application domain that is different from the application domain used by the host.</span></span>  
  
-   <span data-ttu-id="960b1-150">Chaque complément est chargé exclusivement dans son propre domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="960b1-150">Each add-in is loaded exclusively into its own application domain.</span></span> <span data-ttu-id="960b1-151">Il s'agit du niveau d'isolement le plus courant.</span><span class="sxs-lookup"><span data-stu-id="960b1-151">This is the most common level of isolation.</span></span>  
  
-   <span data-ttu-id="960b1-152">Plusieurs compléments sont chargés dans le même domaine d'application dans un processus externe.</span><span class="sxs-lookup"><span data-stu-id="960b1-152">Multiple add-ins are loaded into the same application domain in an external process.</span></span>  
  
-   <span data-ttu-id="960b1-153">Chaque complément est chargé exclusivement dans son propre domaine d'application dans son processus externe.</span><span class="sxs-lookup"><span data-stu-id="960b1-153">Each add-in is loaded exclusively into its own application domain in an external process.</span></span> <span data-ttu-id="960b1-154">Il s'agit du scénario avec le plus d'isolement.</span><span class="sxs-lookup"><span data-stu-id="960b1-154">This is the most isolated scenario.</span></span>  
  
 <span data-ttu-id="960b1-155">Pour plus d’informations sur l’utilisation de processus externes, consultez [Comment : activer des compléments avec différents niveaux d’isolement et de sécurité](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span><span class="sxs-lookup"><span data-stu-id="960b1-155">For more information about using external processes, see [How to: Activate Add-ins with Different Isolation and Security](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span></span>  
  
### <a name="lifetime-management"></a><span data-ttu-id="960b1-156">Gestion de la durée de vie</span><span class="sxs-lookup"><span data-stu-id="960b1-156">Lifetime Management</span></span>  
 <span data-ttu-id="960b1-157">Étant donné que le modèle de complément couvre les limites des domaines d'application et des processus, le garbage collection en lui-même n'est pas suffisant pour libérer et récupérer des objets.</span><span class="sxs-lookup"><span data-stu-id="960b1-157">Because the add-in model spans application domain and process boundaries, garbage collection by itself is not sufficient to release and reclaim objects.</span></span> <span data-ttu-id="960b1-158">Le modèle de complément fournit un mécanisme de gestion de la durée de vie qui utilise des jetons et un comptage des références, et ne requiert généralement pas de programmation supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="960b1-158">The add-in model provides a lifetime management mechanism that uses tokens and reference counting, and usually does not require additional programming.</span></span> <span data-ttu-id="960b1-159">Pour plus d'informations, consultez [Gestion de la durée de vie](http://msdn.microsoft.com/en-us/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span><span class="sxs-lookup"><span data-stu-id="960b1-159">For more information, see [Lifetime Management](http://msdn.microsoft.com/en-us/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span></span>  
  
 [<span data-ttu-id="960b1-160">Retour au début</span><span class="sxs-lookup"><span data-stu-id="960b1-160">Back to top</span></span>](#top)  
  
<a name="distinguishing_between_addins_and_hosts"></a>   
## <a name="distinguishing-between-add-ins-and-hosts"></a><span data-ttu-id="960b1-161">Distinction entre les hôtes et les compléments</span><span class="sxs-lookup"><span data-stu-id="960b1-161">Distinguishing Between Add-ins and Hosts</span></span>  
 <span data-ttu-id="960b1-162">La différence entre un complément et un hôte est simplement que l'hôte est celui qui active le complément.</span><span class="sxs-lookup"><span data-stu-id="960b1-162">The difference between an add-in and a host is merely that the host is the one that activates the add-in.</span></span> <span data-ttu-id="960b1-163">L'hôte peut être le plus important des deux, par exemple une application de traitement de texte et ses vérificateurs d'orthographe, mais l'hôte peut aussi être le moins important des deux, comme un client de messagerie instantanée qui incorpore un lecteur multimédia.</span><span class="sxs-lookup"><span data-stu-id="960b1-163">The host can be the larger of the two, such as a word processing application and its spell checkers; or the host can be the smaller of the two, such as an instant messaging client that embeds a media player.</span></span> <span data-ttu-id="960b1-164">Le modèle de complément prend en charge des compléments dans des scénarios client et serveur.</span><span class="sxs-lookup"><span data-stu-id="960b1-164">The add-in model supports add-ins in both client and server scenarios.</span></span> <span data-ttu-id="960b1-165">Des compléments serveur fournissant des serveurs de messagerie avec analyse antivirus, filtres anti-spam et protection IP sont des exemples de compléments serveur.</span><span class="sxs-lookup"><span data-stu-id="960b1-165">Examples of server add-ins include add-ins that provide mail servers with virus scanning, spam filters, and IP protection.</span></span> <span data-ttu-id="960b1-166">Des compléments de référence pour les traitements de texte, des fonctionnalités spécialisées pour les programmes graphiques et les jeux, et une analyse antivirus pour des clients de messagerie locaux sont des exemples de compléments client.</span><span class="sxs-lookup"><span data-stu-id="960b1-166">Client add-in examples include reference add-ins for word processors, specialized features for graphics programs and games, and virus scanning for local e-mail clients.</span></span>  
  
 [<span data-ttu-id="960b1-167">Retour au début</span><span class="sxs-lookup"><span data-stu-id="960b1-167">Back to top</span></span>](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="960b1-168">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="960b1-168">Related Topics</span></span>  
  
|<span data-ttu-id="960b1-169">Titre</span><span class="sxs-lookup"><span data-stu-id="960b1-169">Title</span></span>|<span data-ttu-id="960b1-170">Description</span><span class="sxs-lookup"><span data-stu-id="960b1-170">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="960b1-171">Pipeline Development</span><span class="sxs-lookup"><span data-stu-id="960b1-171">Pipeline Development</span></span>](../../../docs/framework/add-ins/pipeline-development.md)|<span data-ttu-id="960b1-172">Décrit le pipeline de communication de segments de l'application hôte vers le complément.</span><span class="sxs-lookup"><span data-stu-id="960b1-172">Describes the communication pipeline of segments from the host application to the add-in.</span></span> <span data-ttu-id="960b1-173">Fournit des exemples de code dans des rubriques de procédure pas à pas qui décrivent comment construire le pipeline et déployer des segments vers le pipeline dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="960b1-173">Provides code examples in walkthrough topics that describe how to construct the pipeline and how to deploy segments to the pipeline in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>|  
|[<span data-ttu-id="960b1-174">Domaines d'application et assemblys</span><span class="sxs-lookup"><span data-stu-id="960b1-174">Application Domains and Assemblies</span></span>](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346)|<span data-ttu-id="960b1-175">Décrit la relation entre les domaines d'application, qui fournissent une frontière d'isolement pour la sécurité, la fiabilité et le contrôle de version, et les assemblys.</span><span class="sxs-lookup"><span data-stu-id="960b1-175">Describes the relationship between application domains, which provide an isolation boundary for security, reliability, and versioning, and assemblies.</span></span>|  
  
 [<span data-ttu-id="960b1-176">Retour au début</span><span class="sxs-lookup"><span data-stu-id="960b1-176">Back to top</span></span>](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a><span data-ttu-id="960b1-177">Référence</span><span class="sxs-lookup"><span data-stu-id="960b1-177">Reference</span></span>  
 <xref:System.AddIn?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Contract?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Hosting?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Pipeline?displayProperty=nameWithType>  
  
 [<span data-ttu-id="960b1-178">Retour au début</span><span class="sxs-lookup"><span data-stu-id="960b1-178">Back to top</span></span>](#top)