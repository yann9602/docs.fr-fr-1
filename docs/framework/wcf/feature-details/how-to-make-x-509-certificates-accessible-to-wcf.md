---
title: "Comment : rendre des certificats X.509 accessibles à WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b95ee7c28c67ff861dc401d1405306c78b9663de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="ff476-102">Comment : rendre des certificats X.509 accessibles à WCF</span><span class="sxs-lookup"><span data-stu-id="ff476-102">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="ff476-103">Pour rendre un certificat X.509 accessible à [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], le code d'application doit spécifier le nom et l'emplacement du magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="ff476-103">To make an X.509 certificate accessible to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], application code must specify the certificate store name and location.</span></span> <span data-ttu-id="ff476-104">Dans certains cas, l'identité du processus doit avoir accès au fichier contenant la clé privée associée au certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="ff476-104">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="ff476-105">Pour obtenir la clé privée associée à un certificat X.509 dans un magasin de certificats, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] doit disposer de l'autorisation requise.</span><span class="sxs-lookup"><span data-stu-id="ff476-105">To obtain the private key associated with an X.509 certificate in a certificate store, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] must have permission to do so.</span></span> <span data-ttu-id="ff476-106">Par défaut, seuls le propriétaire et le compte système peuvent accéder à la clé privée d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="ff476-106">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="ff476-107">Pour rendre des certificats X.509 accessibles à WCF</span><span class="sxs-lookup"><span data-stu-id="ff476-107">To make X.509 certificates accessible to WCF</span></span>  
  
1.  <span data-ttu-id="ff476-108">Accordez au compte sous lequel [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'exécute l'accès en lecture au fichier contenant la clé privée associée au certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="ff476-108">Give the account under which [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1.  <span data-ttu-id="ff476-109">Déterminez si [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requiert l'accès en lecture à la clé privée du certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="ff476-109">Determine whether [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="ff476-110">Le tableau suivant précise si une clé privée doit être disponible lors de l'utilisation d'un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="ff476-110">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="ff476-111">Utilisation d'un certificat X.509</span><span class="sxs-lookup"><span data-stu-id="ff476-111">X.509 certificate use</span></span>|<span data-ttu-id="ff476-112">Clé privée</span><span class="sxs-lookup"><span data-stu-id="ff476-112">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="ff476-113">Signature numérique d'un message SOAP sortant.</span><span class="sxs-lookup"><span data-stu-id="ff476-113">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="ff476-114">Oui</span><span class="sxs-lookup"><span data-stu-id="ff476-114">Yes</span></span>|  
        |<span data-ttu-id="ff476-115">Vérification de la signature d'un message SOAP entrant.</span><span class="sxs-lookup"><span data-stu-id="ff476-115">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="ff476-116">Non</span><span class="sxs-lookup"><span data-stu-id="ff476-116">No</span></span>|  
        |<span data-ttu-id="ff476-117">Chiffrement d'un message SOAP sortant.</span><span class="sxs-lookup"><span data-stu-id="ff476-117">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="ff476-118">Non</span><span class="sxs-lookup"><span data-stu-id="ff476-118">No</span></span>|  
        |<span data-ttu-id="ff476-119">Déchiffrement d'un message SOAP entrant.</span><span class="sxs-lookup"><span data-stu-id="ff476-119">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="ff476-120">Oui</span><span class="sxs-lookup"><span data-stu-id="ff476-120">Yes</span></span>|  
  
    2.  <span data-ttu-id="ff476-121">Déterminez l'emplacement et le nom du magasin de certificats dans lequel le certificat est stocké.</span><span class="sxs-lookup"><span data-stu-id="ff476-121">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="ff476-122">Le magasin de certificats dans lequel le certificat est stocké est spécifié dans le code d'application ou dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="ff476-122">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="ff476-123">Ainsi, l'exemple suivant spécifie que le certificat se trouve dans le magasin de certificats `CurrentUser` nommé `My`.</span><span class="sxs-lookup"><span data-stu-id="ff476-123">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3.  <span data-ttu-id="ff476-124">Déterminer où la clé privée pour le certificat se trouve sur l’ordinateur à l’aide de la [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) outil.</span><span class="sxs-lookup"><span data-stu-id="ff476-124">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="ff476-125">Le [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) outil nécessite le nom du magasin de certificat et emplacement du magasin de certificats quelque chose qui identifie de façon unique le certificat.</span><span class="sxs-lookup"><span data-stu-id="ff476-125">The [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="ff476-126">Il accepte le nom de sujet du certificat ou son empreinte numérique comme identificateur unique.</span><span class="sxs-lookup"><span data-stu-id="ff476-126">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ff476-127">Comment déterminer l’empreinte numérique d’un certificat, consultez [Comment : récupérer l’empreinte numérique d’un certificat](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="ff476-127"> how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="ff476-128">Le de code suivant montre comment utiliser le [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) outil pour déterminer l’emplacement de la clé privée d’un certificat dans le `My` stocker dans `CurrentUser` avec une empreinte numérique de `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span><span class="sxs-lookup"><span data-stu-id="ff476-128">The following code example uses the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```  
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4.  <span data-ttu-id="ff476-129">Déterminez le compte sous lequel [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'exécute.</span><span class="sxs-lookup"><span data-stu-id="ff476-129">Determine the account that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is running under.</span></span>  
  
         <span data-ttu-id="ff476-130">Le tableau suivant précise le compte sous lequel [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'exécute pour un scénario donné.</span><span class="sxs-lookup"><span data-stu-id="ff476-130">The following table details the account under which [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="ff476-131">Scénario</span><span class="sxs-lookup"><span data-stu-id="ff476-131">Scenario</span></span>|<span data-ttu-id="ff476-132">Identité du processus</span><span class="sxs-lookup"><span data-stu-id="ff476-132">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="ff476-133">Client (console ou application WinForms).</span><span class="sxs-lookup"><span data-stu-id="ff476-133">Client (console or WinForms application).</span></span>|<span data-ttu-id="ff476-134">Utilisateur actuellement connecté.</span><span class="sxs-lookup"><span data-stu-id="ff476-134">Currently logged in user.</span></span>|  
        |<span data-ttu-id="ff476-135">Service auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="ff476-135">Service that is self-hosted.</span></span>|<span data-ttu-id="ff476-136">Utilisateur actuellement connecté.</span><span class="sxs-lookup"><span data-stu-id="ff476-136">Currently logged in user.</span></span>|  
        |<span data-ttu-id="ff476-137">Service hébergé dans IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) ou IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="ff476-137">Service that is hosted in IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) or IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span></span>|<span data-ttu-id="ff476-138">SERVICE RÉSEAU</span><span class="sxs-lookup"><span data-stu-id="ff476-138">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="ff476-139">Service hébergé dans IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="ff476-139">Service that is hosted in IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span></span>|<span data-ttu-id="ff476-140">Contrôlé par l'élément `<processModel>` dans le fichier Machine.config.</span><span class="sxs-lookup"><span data-stu-id="ff476-140">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="ff476-141">Le compte par défaut est ASPNET.</span><span class="sxs-lookup"><span data-stu-id="ff476-141">The default account is ASPNET.</span></span>|  
  
    5.  <span data-ttu-id="ff476-142">Accordez l'accès en lecture au fichier contenant la clé privée du compte sous lequel [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'exécute, à l'aide d'un outil tel que cacls.exe.</span><span class="sxs-lookup"><span data-stu-id="ff476-142">Grant read access to the file that contains the private key to the account that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is running under, using a tool such as cacls.exe.</span></span>  
  
         <span data-ttu-id="ff476-143">L'exemple de code suivant modifie (/E) la liste de contrôle d'accès (ACL) du fichier spécifié pour accorder (/G) au compte SERVICE RÉSEAU l'accès en lecture (: R) au fichier.</span><span class="sxs-lookup"><span data-stu-id="ff476-143">The following code example edits (/E) the access control list (ACL) for the specified file to grant (/G) the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```  
        cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="ff476-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff476-144">See Also</span></span>  
 [<span data-ttu-id="ff476-145">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="ff476-145">FindPrivateKey</span></span>](../../../../docs/framework/wcf/samples/findprivatekey.md)  
 [<span data-ttu-id="ff476-146">Guide pratique pour récupérer l’empreinte numérique d’un certificat</span><span class="sxs-lookup"><span data-stu-id="ff476-146">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)  
 [<span data-ttu-id="ff476-147">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="ff476-147">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
