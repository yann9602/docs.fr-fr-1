---
title: "Comment : sécuriser des messages au sein de sessions fiables"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 3f27b1a4de2019660e0facb081300a79eae65b99
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="cf527-102">Comment : sécuriser des messages au sein de sessions fiables</span><span class="sxs-lookup"><span data-stu-id="cf527-102">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="cf527-103">Cette rubrique décrit les étapes requises pour activer la sécurité au niveau du message pour les messages échangés dans une session fiable utilisant l’une des liaisons fournies par le système qui prennent en charge une telle session, mais pas par défaut.</span><span class="sxs-lookup"><span data-stu-id="cf527-103">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="cf527-104">Activer une session sécurisée et fiable, soit impérativement en utilisant du code ou de façon déclarative dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="cf527-104">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="cf527-105">Cette procédure utilise le client et les fichiers de configuration du service pour activer la session fiable sécurisée.</span><span class="sxs-lookup"><span data-stu-id="cf527-105">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="cf527-106">La procédure inclut les trois tâches clés suivantes :</span><span class="sxs-lookup"><span data-stu-id="cf527-106">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="cf527-107">Spécifiez que le client et le service échangent des messages dans une session fiable.</span><span class="sxs-lookup"><span data-stu-id="cf527-107">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="cf527-108">Requérez la sécurité au niveau du message dans la session fiable.</span><span class="sxs-lookup"><span data-stu-id="cf527-108">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="cf527-109">Spécifiez le type d'informations d'identification que le client doit utiliser pour être authentifié auprès du service.</span><span class="sxs-lookup"><span data-stu-id="cf527-109">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="cf527-110">Il est important dans la première tâche que l’élément de configuration de point de terminaison contienne un `bindingConfiguration` attribut qui fait référence à une configuration de liaison nommée (dans cet exemple) `MessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="cf527-110">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="cf527-111">Le [  **\<liaison >** ](../../../../docs/framework/misc/binding.md) élément de configuration puis référence ce nom pour activer les sessions fiables en définissant le `enabled` attribut de la [  **\<reliableSession >** ](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) élément `true`.</span><span class="sxs-lookup"><span data-stu-id="cf527-111">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) element to `true`.</span></span> <span data-ttu-id="cf527-112">Vous pouvez requérir que les assurances de remise ordonnée soient disponibles dans une session fiable en affectant à l'attribut `ordered` la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="cf527-112">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="cf527-113">Pour la copie de la source de l’exemple sur lequel repose cette procédure de configuration, consultez le [Session fiable de WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="cf527-113">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="cf527-114">Les éléments essentiels de la seconde tâche sont effectuées en définissant le `mode` attribut de la  **\<sécurité >** élément contenu dans le  **\<liaison >** élément du client et du service à `Message`.</span><span class="sxs-lookup"><span data-stu-id="cf527-114">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="cf527-115">Les éléments essentiels de la troisième tâche sont effectuées en définissant le `clientCredentialType` attribut de la  **\<message >** élément contenu dans le  **\<sécurité >** élément du client et du service à `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="cf527-115">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="cf527-116">Lorsque vous utilisez la sécurité des messages avec les sessions fiables, une messagerie fiable tente d’authentifier un client non authentifié jusqu'à ce qu’un délai d’attente se produit au lieu de lever une exception sur premier échec.</span><span class="sxs-lookup"><span data-stu-id="cf527-116">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="cf527-117">Configurer le service avec une liaison WSHttpBinding afin d’utiliser une session fiable</span><span class="sxs-lookup"><span data-stu-id="cf527-117">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="cf527-118">Cette procédure est décrite dans [Comment : échange de Messages au sein d’une Session fiable](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="cf527-118">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="cf527-119">Configurer le client avec une liaison WSHttpBinding afin d’utiliser une session fiable</span><span class="sxs-lookup"><span data-stu-id="cf527-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="cf527-120">Cette procédure est décrite dans [Comment : échange de Messages au sein d’une Session fiable](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="cf527-120">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="cf527-121">Définir le mode et le ClientCredentialType dans la configuration</span><span class="sxs-lookup"><span data-stu-id="cf527-121">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="cf527-122">Ajouter un élément de liaison approprié à la [  **\<liaisons >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) élément du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="cf527-122">Add an appropriate binding element to the [**\<bindings>**](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="cf527-123">L’exemple suivant ajoute un [  **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) élément.</span><span class="sxs-lookup"><span data-stu-id="cf527-123">The following example adds a [**\<wsHttpBinding>**](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="cf527-124">Ajouter un  **\<liaison >** et définissez son `name` attribut une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="cf527-124">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="cf527-125">L’exemple utilise le nom `MessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="cf527-125">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="cf527-126">Ajouter un  **\<sécurité >** et affectez le `mode` attribut `Message`.</span><span class="sxs-lookup"><span data-stu-id="cf527-126">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="cf527-127">Dans le  **\<sécurité >** élément, ajouter un  **\<message >** et affectez le `clientCredentialType` attribut `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="cf527-127">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
