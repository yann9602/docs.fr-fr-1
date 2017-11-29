---
title: "Comment : référencer des certificats X.509 de manière cohérente"
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
helpviewer_keywords: certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8d42af919b9792fc5a5303737187be7ffef6405d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-consistently-reference-x509-certificates"></a><span data-ttu-id="5016a-102">Comment : référencer des certificats X.509 de manière cohérente</span><span class="sxs-lookup"><span data-stu-id="5016a-102">How to: Consistently Reference X.509 Certificates</span></span>
<span data-ttu-id="5016a-103">Vous pouvez identifier un certificat de plusieurs manières : par le hachage du certificat, par l'émetteur et le numéro de série ou par l'identificateur de la clé du sujet.</span><span class="sxs-lookup"><span data-stu-id="5016a-103">You can identify a certificate in several ways: by the hash of the certificate, by the issuer and serial number, or by the subject key identifier (SKI).</span></span> <span data-ttu-id="5016a-104">L'identificateur de la clé du sujet fournit une identification unique de la clé publique du sujet du certificat et sert souvent dans le cadre des signatures numériques XML.</span><span class="sxs-lookup"><span data-stu-id="5016a-104">The SKI provides a unique identification for the certificate's subject public key and is often used when working with XML digital signing.</span></span> <span data-ttu-id="5016a-105">La valeur de cet identificateur fait habituellement partie du certificat X.509 sous une *extension de certificat X.509*.</span><span class="sxs-lookup"><span data-stu-id="5016a-105">The SKI value is usually part of the X.509 certificate as an *X.509 certificate extension*.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="5016a-106">a une valeur par défaut *style de référencement* qui utilise l’émetteur et le numéro de série si l’extension SKI est manquante sur le certificat.</span><span class="sxs-lookup"><span data-stu-id="5016a-106"> has a default *referencing style* that uses the issuer and serial number if the SKI extension is missing from the certificate.</span></span> <span data-ttu-id="5016a-107">Si le certificat contient l’extension de l’identificateur, le style de référencement utilise par défaut l’identificateur pour pointer vers le certificat.</span><span class="sxs-lookup"><span data-stu-id="5016a-107">If the certificate contains the SKI extension, the default referencing style uses the SKI to point to the certificate.</span></span> <span data-ttu-id="5016a-108">Si, au cours du développement d'une application, vous passez de certificats qui n'utilisent pas l'extension de l'identificateur à des certificats qui l'utilisent, le style de référencement utilisé dans les messages générés par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] change également.</span><span class="sxs-lookup"><span data-stu-id="5016a-108">If mid-way through development of an application, you switch from using certificates that do not use the SKI extension to certificates that use the SKI extension, the referencing style used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-generated messages also changes.</span></span>  
  
 <span data-ttu-id="5016a-109">Si un style de référencement cohérent est requis indépendamment de la présence de l’extension de l’identificateur de la clé du sujet, il est possible de configurer ce style de référencement souhaité comme l’illustre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="5016a-109">If a consistent referencing style is required regardless of SKI extension presence, it is possible to configure the desired referencing style as shown in the following code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5016a-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="5016a-110">Example</span></span>  
 <span data-ttu-id="5016a-111">L’exemple suivant crée un élément de liaison de sécurité personnalisé qui utilise un seul style de référencement cohérent, le nom de l’émetteur et le numéro de série.</span><span class="sxs-lookup"><span data-stu-id="5016a-111">The following example creates a custom security binding element that uses a single consistent referencing style, the issuer name and serial number.</span></span>  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5016a-112">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="5016a-112">Compiling the Code</span></span>  
 <span data-ttu-id="5016a-113">Les espaces de noms suivants sont requis pour compiler le code :</span><span class="sxs-lookup"><span data-stu-id="5016a-113">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a><span data-ttu-id="5016a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5016a-114">See Also</span></span>  
 [<span data-ttu-id="5016a-115">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="5016a-115">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
