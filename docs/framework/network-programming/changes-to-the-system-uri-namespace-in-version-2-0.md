---
title: "Modifications apportées à l’espace de noms System.Uri dans la Version 2.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 906abbcbd3ec00e76d8c183f61828fb5135d9154
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a><span data-ttu-id="113f2-102">Modifications apportées à l’espace de noms System.Uri dans la Version 2.0</span><span class="sxs-lookup"><span data-stu-id="113f2-102">Changes to the System.Uri namespace in Version 2.0</span></span>
<span data-ttu-id="113f2-103">Plusieurs modifications ont été apportées à la classe <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="113f2-103">Several changes were made to the <xref:System.Uri?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="113f2-104">Ces modifications éliminent un comportement incorrect, améliorent la convivialité et renforcent la sécurité.</span><span class="sxs-lookup"><span data-stu-id="113f2-104">These changes fixed incorrect behavior, enhanced usability, and enhanced security.</span></span>  
  
## <a name="obsolete-and-deprecated-members"></a><span data-ttu-id="113f2-105">Membres obsolètes et dépréciés</span><span class="sxs-lookup"><span data-stu-id="113f2-105">Obsolete and Deprecated Members</span></span>  
 <span data-ttu-id="113f2-106">Constructeurs :</span><span class="sxs-lookup"><span data-stu-id="113f2-106">Constructors:</span></span>  
  
-   <span data-ttu-id="113f2-107">Tous les constructeurs qui ont un paramètre `dontEscape`.</span><span class="sxs-lookup"><span data-stu-id="113f2-107">All constructors that have a `dontEscape` parameter.</span></span>  
  
 <span data-ttu-id="113f2-108">Méthodes :</span><span class="sxs-lookup"><span data-stu-id="113f2-108">Methods:</span></span>  
  
-   <xref:System.Uri.CheckSecurity%2A>  
  
-   <xref:System.Uri.Escape%2A>  
  
-   <xref:System.Uri.Canonicalize%2A>  
  
-   <xref:System.Uri.Parse%2A>  
  
-   <xref:System.Uri.IsReservedCharacter%2A>  
  
-   <xref:System.Uri.IsBadFileSystemCharacter%2A>  
  
-   <xref:System.Uri.IsExcludedCharacter%2A>  
  
-   <xref:System.Uri.EscapeString%2A>  
  
## <a name="changes"></a><span data-ttu-id="113f2-109">Modifications</span><span class="sxs-lookup"><span data-stu-id="113f2-109">Changes</span></span>  
  
-   <span data-ttu-id="113f2-110">Pour les schémas d’URI qui sont connus comme n’ayant aucune partie de requête (file, ftp, etc.), le caractère « ? » est toujours placé dans une séquence d’échappement et n’est pas considéré comme le début d’une partie <xref:System.Uri.Query%2A>.</span><span class="sxs-lookup"><span data-stu-id="113f2-110">For URI schemes that are known to not have a query part (file, ftp, and others), the '?' character is always escaped and is not considered the beginning of a <xref:System.Uri.Query%2A> part.</span></span>  
  
-   <span data-ttu-id="113f2-111">Pour les URI de fichiers implicites (au format « c:\directory\file@name.txt »), le caractère de fragment (« # ») est toujours placé dans une séquence d’échappement, sauf si l’absence totale de séquence d’échappement est demandée ou si <xref:System.Uri.LocalPath%2A> est `true`.</span><span class="sxs-lookup"><span data-stu-id="113f2-111">For implicit file URIs (of the form "c:\directory\file@name.txt"), the fragment character ('#') is always escaped unless full unescaping is requested or <xref:System.Uri.LocalPath%2A> is `true`.</span></span>  
  
-   <span data-ttu-id="113f2-112">La prise en charge des noms d’hôtes UNC a été supprimée ; la spécification IDN pour la représentation des noms d’hôtes internationaux a été adoptée.</span><span class="sxs-lookup"><span data-stu-id="113f2-112">UNC hostname support was removed; the IDN specification for representing international hostnames was adopted.</span></span>  
  
-   <span data-ttu-id="113f2-113"><xref:System.Uri.LocalPath%2A> retourne toujours une chaîne sans séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="113f2-113"><xref:System.Uri.LocalPath%2A> always returns a completely unescaped string.</span></span>  
  
-   <span data-ttu-id="113f2-114"><xref:System.Uri.ToString%2A> ne supprime pas la séquence d’échappement d’un caractère « % », « ? » ou « # » placé dans une séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="113f2-114"><xref:System.Uri.ToString%2A> does not unescape an escaped '%', '?', or '#' character.</span></span>  
  
-   <span data-ttu-id="113f2-115"><xref:System.Uri.Equals%2A> inclut désormais la partie <xref:System.Uri.Query%2A> dans la vérification de l’égalité.</span><span class="sxs-lookup"><span data-stu-id="113f2-115"><xref:System.Uri.Equals%2A> now includes the <xref:System.Uri.Query%2A> part in the equality check.</span></span>  
  
-   <span data-ttu-id="113f2-116">Les opérateurs « = » et « != » sont substitués et liés à la méthode <xref:System.Uri.Equals%2A>.</span><span class="sxs-lookup"><span data-stu-id="113f2-116">Operators "==" and "!=" are overridden and linked to the <xref:System.Uri.Equals%2A> method.</span></span>  
  
-   <span data-ttu-id="113f2-117"><xref:System.Uri.IsLoopback%2A> produit maintenant des résultats cohérents.</span><span class="sxs-lookup"><span data-stu-id="113f2-117"><xref:System.Uri.IsLoopback%2A> now produces consistent results.</span></span>  
  
-   <span data-ttu-id="113f2-118">L’URI « `file:///path` » n’est plus traduite en « file://path ».</span><span class="sxs-lookup"><span data-stu-id="113f2-118">The URI "`file:///path`" is no longer translated into "file://path".</span></span>  
  
-   <span data-ttu-id="113f2-119">« # » est maintenant reconnu comme un terminateur de nom d’hôte.</span><span class="sxs-lookup"><span data-stu-id="113f2-119">"#" is now recognized as a host name terminator.</span></span> <span data-ttu-id="113f2-120">Autrement dit, « http://consoto.com#fragment » est désormais converti en « http://contoso.com/#fragment ».</span><span class="sxs-lookup"><span data-stu-id="113f2-120">That is, "http://consoto.com#fragment" is now converted to "http://contoso.com/#fragment".</span></span>  
  
-   <span data-ttu-id="113f2-121">Un bogue présent lors de la combinaison d’un URI de base avec un fragment a été résolu.</span><span class="sxs-lookup"><span data-stu-id="113f2-121">A bug when combining a base URI with a fragment has been fixed.</span></span>  
  
-   <span data-ttu-id="113f2-122">Un bogue dans <xref:System.Uri.HostNameType%2A> a été résolu.</span><span class="sxs-lookup"><span data-stu-id="113f2-122">A bug in <xref:System.Uri.HostNameType%2A> is fixed.</span></span>  
  
-   <span data-ttu-id="113f2-123">Un bogue dans l’analyse NNTP a été résolu.</span><span class="sxs-lookup"><span data-stu-id="113f2-123">A bug in NNTP parsing is fixed.</span></span>  
  
-   <span data-ttu-id="113f2-124">Un URI au format HTTP:contoso.com lève désormais une exception d’analyse.</span><span class="sxs-lookup"><span data-stu-id="113f2-124">A URI of the form HTTP:contoso.com now throws a parsing exception.</span></span>  
  
-   <span data-ttu-id="113f2-125">Le Framework gère correctement userinfo dans un URI.</span><span class="sxs-lookup"><span data-stu-id="113f2-125">The Framework correctly handles userinfo in a URI.</span></span>  
  
-   <span data-ttu-id="113f2-126">La compression de chemin d’URI a été résolue afin qu’un URI rompu ne puisse pas parcourir le système de fichiers au-dessus de la racine.</span><span class="sxs-lookup"><span data-stu-id="113f2-126">URI path compression is fixed so that a broken URI cannot traverse the file system above the root.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="113f2-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="113f2-127">See Also</span></span>  
 <xref:System.Uri?displayProperty=nameWithType>
