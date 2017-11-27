---
title: "Combinaison de protocoles d'approbation dans les scénarios fédérés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 007dec81766423ea2826e98ae0b6b399a1508f11
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="d4609-102">Combinaison de protocoles d'approbation dans les scénarios fédérés</span><span class="sxs-lookup"><span data-stu-id="d4609-102">Mixing Trust Protocols in Federated Scenarios</span></span>
<span data-ttu-id="d4609-103">Il peut exister des scénarios où des clients fédérés communiquent avec un WSDL de service et un service de jeton de sécurité (STS) qui n'ont pas la même version d'approbation.</span><span class="sxs-lookup"><span data-stu-id="d4609-103">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="d4609-104">Le WSDL de service peut contenir une assertion `RequestSecurityTokenTemplate` avec les éléments WS-Trust qui sont de versions différentes par rapport à STS.</span><span class="sxs-lookup"><span data-stu-id="d4609-104">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="d4609-105">Dans ce cas, un client [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] convertit les éléments WS-Trust reçus depuis `RequestSecurityTokenTemplate` de façon à ce qu'ils correspondent à la version d'approbation de STS.</span><span class="sxs-lookup"><span data-stu-id="d4609-105">In such cases, a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d4609-106"> gère les versions d'approbation qui ne correspondent pas uniquement pour les liaisons standard.</span><span class="sxs-lookup"><span data-stu-id="d4609-106"> handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="d4609-107">Tous les paramètres d'algorithme standard reconnus par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] font partie de la liaison standard.</span><span class="sxs-lookup"><span data-stu-id="d4609-107">All standard algorithm parameters that are recognized by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are part of the standard binding.</span></span> <span data-ttu-id="d4609-108">Cette rubrique décrit le comportement de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec divers paramètres d'approbation entre le service et STS.</span><span class="sxs-lookup"><span data-stu-id="d4609-108">This topic describes the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="d4609-109">RP février 2005 et STS février 2005</span><span class="sxs-lookup"><span data-stu-id="d4609-109">RP Feb 2005 and STS Feb 2005</span></span>  
 <span data-ttu-id="d4609-110">Le WSDL pour la partie de confiance (RP) contient les éléments suivants dans la section `RequestSecurityTokenTemplate` :</span><span class="sxs-lookup"><span data-stu-id="d4609-110">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="d4609-111">Le fichier de configuration client contient une liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="d4609-111">The client configuration file contains a list of parameters.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d4609-112"> ne peut pas différencier les paramètres du client des paramètres du service ; il ajoute tous les paramètres et les envoie dans `RequestSecurityTokenTemplate` (RST).</span><span class="sxs-lookup"><span data-stu-id="d4609-112"> cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="d4609-113">Version d'approbation RP 1.3 et Version d'approbation STS 1.3</span><span class="sxs-lookup"><span data-stu-id="d4609-113">RP Trust 1.3 and STS Trust 1.3</span></span>  
 <span data-ttu-id="d4609-114">Le WSDL pour la partie de confiance (RP) contient les éléments suivants dans la section `RequestSecurityTokenTemplate` :</span><span class="sxs-lookup"><span data-stu-id="d4609-114">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="d4609-115">Le fichier de configuration client contient un élément `secondaryParameters` qui encapsule les paramètres spécifié par la partie de confiance.</span><span class="sxs-lookup"><span data-stu-id="d4609-115">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d4609-116"> supprime les éléments `EncryptionAlgorithm`, `CanonicalizationAlgorithm` et `KeyWrapAlgorithm` de l'élément de niveau supérieur sous le RST si ceux-ci sont présents dans l'élément `SecondaryParameters`.</span><span class="sxs-lookup"><span data-stu-id="d4609-116"> removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d4609-117"> ajoute l'élément `SecondaryParameters` au RST sortant non modifié.</span><span class="sxs-lookup"><span data-stu-id="d4609-117"> appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="d4609-118">Version d'approbation RP février 2005 et Version d'approbation STS 1.3</span><span class="sxs-lookup"><span data-stu-id="d4609-118">RP Trust Feb 2005 and STS Trust 1.3</span></span>  
 <span data-ttu-id="d4609-119">Le WSDL pour la partie de confiance (RP) contient les éléments suivants dans la section `RequestSecurityTokenTemplate` :</span><span class="sxs-lookup"><span data-stu-id="d4609-119">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="d4609-120">Le fichier de configuration client contient une liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="d4609-120">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="d4609-121">À partir du fichier de configuration client, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne peut pas différencier les paramètres du service de ceux du client.</span><span class="sxs-lookup"><span data-stu-id="d4609-121">From the client configuration file, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="d4609-122">Par conséquent, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] convertit tous les paramètres en un espace de noms de version d'approbation 1.3.</span><span class="sxs-lookup"><span data-stu-id="d4609-122">Therefore [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d4609-123"> gère les éléments `KeyType`, `KeySize` et `TokenType` comme suit :</span><span class="sxs-lookup"><span data-stu-id="d4609-123"> handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
-   <span data-ttu-id="d4609-124">Téléchargez le WSDL, créez la liaison et assignez `KeyType`, `KeySize` et `TokenType` à partir des paramètres RP.</span><span class="sxs-lookup"><span data-stu-id="d4609-124">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="d4609-125">Le fichier de configuration client est alors généré.</span><span class="sxs-lookup"><span data-stu-id="d4609-125">The client configuration file is then generated.</span></span>  
  
-   <span data-ttu-id="d4609-126">Le client peut maintenant modifier tout paramètre dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="d4609-126">The client can now change any parameter in the configuration file.</span></span>  
  
-   <span data-ttu-id="d4609-127">Pendant l'exécution, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] copie tous les paramètres spécifiés dans la section `AdditionalTokenParameters` du fichier de configuration client sauf `KeyType`, `KeySize` et `TokenType` car ces paramètres sont pris en compte pendant la génération du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="d4609-127">During runtime, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="d4609-128">Version d'approbation RP 1.3 et Version d'approbation STS février 2005</span><span class="sxs-lookup"><span data-stu-id="d4609-128">RP Trust 1.3 and STS Trust Feb 2005</span></span>  
 <span data-ttu-id="d4609-129">Le WSDL pour la partie de confiance (RP) contient les éléments suivants dans la section `RequestSecurityTokenTemplate` :</span><span class="sxs-lookup"><span data-stu-id="d4609-129">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="d4609-130">Le fichier de configuration client contient un élément `secondaryParamters` qui encapsule les paramètres spécifié par la partie de confiance.</span><span class="sxs-lookup"><span data-stu-id="d4609-130">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d4609-131"> copie tous les paramètres spécifiés dans la section `SecondaryParameters` dans l'élément RST de niveau supérieur, mais ne les convertit pas en espace de noms WS-Trust 2005.</span><span class="sxs-lookup"><span data-stu-id="d4609-131"> copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
