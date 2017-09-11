---
title: Certmgr.exe (outil de gestionnaire de certificats)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- certificates, managing
- CRLs
- certificate trust lists
- Certmgr.exe
- Certificate Manager tool
- CTLs
- certificate revocation lists
ms.assetid: 7e953b43-1374-4bbc-814f-53ca1b6b52bb
caps.latest.revision: 27
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: bd5d1011a8f8aeadfc7729c3a4f6f56a033110a9
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="certmgrexe-certificate-manager-tool"></a><span data-ttu-id="2a59f-102">Certmgr.exe (outil de gestionnaire de certificats)</span><span class="sxs-lookup"><span data-stu-id="2a59f-102">Certmgr.exe (Certificate Manager Tool)</span></span>
<span data-ttu-id="2a59f-103">L'outil Certificate Manager (Certmgr.exe) gère les certificats, les listes de certificats de confiance (CTL) et les listes de révocation de certificats (CRL).</span><span class="sxs-lookup"><span data-stu-id="2a59f-103">The Certificate Manager tool (Certmgr.exe) manages certificates, certificate trust lists (CTLs), and certificate revocation lists (CRLs).</span></span>  
  
 <span data-ttu-id="2a59f-104">Cet outil est installé automatiquement avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2a59f-104">The Certificate Manager is automatically installed with Visual Studio.</span></span> <span data-ttu-id="2a59f-105">Pour démarrer l’outil, utilisez des [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="2a59f-105">To start the tool, use the [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a59f-106">L'outil Certificate Manager (Certmgr.exe) est un utilitaire en ligne de commande, alors que Certificats (Certmgr.msc) est un composant logiciel enfichable MMC (Microsoft Management Console).</span><span class="sxs-lookup"><span data-stu-id="2a59f-106">The Certificate Manager tool (Certmgr.exe) is a command-line utility, whereas Certificates (Certmgr.msc) is a Microsoft Management Console (MMC) snap-in.</span></span> <span data-ttu-id="2a59f-107">Étant donné que Certmgr.msc se trouve généralement dans le répertoire système de Windows, la saisie de `certmgr` sur la ligne de commande peut charger le composant logiciel enfichable MMC Certificats et ce, même si vous avez ouvert l'invite de commandes Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2a59f-107">Because Certmgr.msc is usually found in the Windows System directory, entering `certmgr` at the command line may load the Certificates MMC snap-in even if you have opened the Visual Studio Command Prompt.</span></span> <span data-ttu-id="2a59f-108">Cela se produit parce que le chemin d’accès au composant logiciel enfichable précède le chemin d’accès à l’outil Certificate Manager dans la variable d’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="2a59f-108">This occurs because the path to the snap-in precedes the path to the Certificate Manager tool in the PATH environment variable.</span></span> <span data-ttu-id="2a59f-109">Si vous rencontrez ce problème, vous pouvez exécuter des commandes Certmgr.exe en spécifiant le chemin d'accès au fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="2a59f-109">If you encounter this problem, you can execute Certmgr.exe commands by specifying the path to the executable.</span></span>  
  
 <span data-ttu-id="2a59f-110">Cet outil est installé automatiquement avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2a59f-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="2a59f-111">Pour exécuter l'outil, utilisez l'invite de commandes développeur (ou l'invite de commandes Visual Studio dans Windows 7).</span><span class="sxs-lookup"><span data-stu-id="2a59f-111">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="2a59f-112">Pour plus d'informations, consultez [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="2a59f-112">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="2a59f-113">Pour une vue d'ensemble des certificats X.509, consultez [Utilisation des certificats](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="2a59f-113">For an overview of X.509 certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
 <span data-ttu-id="2a59f-114">À l'invite de commandes, tapez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="2a59f-114">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a59f-115">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a59f-115">Syntax</span></span>  
  
```  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a59f-116">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2a59f-116">Parameters</span></span>  
  
|<span data-ttu-id="2a59f-117">Argument</span><span class="sxs-lookup"><span data-stu-id="2a59f-117">Argument</span></span>|<span data-ttu-id="2a59f-118">Description</span><span class="sxs-lookup"><span data-stu-id="2a59f-118">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="2a59f-119">*sourceStorename*</span><span class="sxs-lookup"><span data-stu-id="2a59f-119">*sourceStorename*</span></span>|<span data-ttu-id="2a59f-120">Le magasin de certificats qui contient les certificats existants, les CTL ou CRL à ajouter, supprimer, enregistrer ou afficher.</span><span class="sxs-lookup"><span data-stu-id="2a59f-120">The certificate store that contains the existing certificates, CTLs, or CRLs to add, delete, save, or display.</span></span> <span data-ttu-id="2a59f-121">Il peut s'agir d'un fichier de magasin ou d'un magasin système.</span><span class="sxs-lookup"><span data-stu-id="2a59f-121">This can be a store file or a systems store.</span></span>|  
|<span data-ttu-id="2a59f-122">*destinationStorename*</span><span class="sxs-lookup"><span data-stu-id="2a59f-122">*destinationStorename*</span></span>|<span data-ttu-id="2a59f-123">Magasin ou fichier du certificat de sortie.</span><span class="sxs-lookup"><span data-stu-id="2a59f-123">The output certificate store or file.</span></span>|  
  
|<span data-ttu-id="2a59f-124">Option</span><span class="sxs-lookup"><span data-stu-id="2a59f-124">Option</span></span>|<span data-ttu-id="2a59f-125">Description</span><span class="sxs-lookup"><span data-stu-id="2a59f-125">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="2a59f-126">**/add**</span><span class="sxs-lookup"><span data-stu-id="2a59f-126">**/add**</span></span>|<span data-ttu-id="2a59f-127">Ajoute des certificats, listes de certificats de confiance et listes de révocation de certificats à un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="2a59f-127">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>|  
|<span data-ttu-id="2a59f-128">**/all**</span><span class="sxs-lookup"><span data-stu-id="2a59f-128">**/all**</span></span>|<span data-ttu-id="2a59f-129">Ajoute toutes les entrées si utilisée avec **/add**.</span><span class="sxs-lookup"><span data-stu-id="2a59f-129">Adds all entries when used with **/add**.</span></span> <span data-ttu-id="2a59f-130">Supprime toutes les entrées si utilisée avec **/del**.</span><span class="sxs-lookup"><span data-stu-id="2a59f-130">Deletes all entries when used with **/del**.</span></span> <span data-ttu-id="2a59f-131">Affiche toutes les entrées si utilisée sans les options **/add**, ni **/del**.</span><span class="sxs-lookup"><span data-stu-id="2a59f-131">Displays all entries when used without the **/add** or **/del** options.</span></span> <span data-ttu-id="2a59f-132">L'option **/all** ne peut pas être utilisée avec **/put**.</span><span class="sxs-lookup"><span data-stu-id="2a59f-132">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="2a59f-133">**/c**</span><span class="sxs-lookup"><span data-stu-id="2a59f-133">**/c**</span></span>|<span data-ttu-id="2a59f-134">Ajoute des certificats si utilisée avec **/add**.</span><span class="sxs-lookup"><span data-stu-id="2a59f-134">Adds certificates when used with **/add**.</span></span> <span data-ttu-id="2a59f-135">Supprime des certificats si utilisée avec **/del**.</span><span class="sxs-lookup"><span data-stu-id="2a59f-135">Deletes certificates when used with **/del**.</span></span> <span data-ttu-id="2a59f-136">Enregistre des certificats si utilisée avec **/put**.</span><span class="sxs-lookup"><span data-stu-id="2a59f-136">Saves certificates when used with **/put**.</span></span> <span data-ttu-id="2a59f-137">Affiche des certificats si utilisée sans les options **/add**, **/del** ou **/put**.</span><span class="sxs-lookup"><span data-stu-id="2a59f-137">Displays certificates when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="2a59f-138">**/CRL**</span><span class="sxs-lookup"><span data-stu-id="2a59f-138">**/CRL**</span></span>|<span data-ttu-id="2a59f-139">Ajoute des listes de révocation de certificats si utilisée avec **/add**.</span><span class="sxs-lookup"><span data-stu-id="2a59f-139">Adds CRLs when used with **/add**.</span></span> <span data-ttu-id="2a59f-140">Supprime des listes de révocation de certificats si utilisée avec **/del**.</span><span class="sxs-lookup"><span data-stu-id="2a59f-140">Deletes CRLs when used with **/del**.</span></span> <span data-ttu-id="2a59f-141">Enregistre des listes de révocation de certificats si utilisée avec **/put**.</span><span class="sxs-lookup"><span data-stu-id="2a59f-141">Saves CRLs when used with **/put**.</span></span> <span data-ttu-id="2a59f-142">Affiche les listes de révocation des certificats si utilisée sans les options **/add**, **/del** ou **/put**.</span><span class="sxs-lookup"><span data-stu-id="2a59f-142">Displays CRLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="2a59f-143">**/CTL**</span><span class="sxs-lookup"><span data-stu-id="2a59f-143">**/CTL**</span></span>|<span data-ttu-id="2a59f-144">Ajoute des listes de certificats de confiance si utilisée avec **/add**.</span><span class="sxs-lookup"><span data-stu-id="2a59f-144">Adds CTLs when used with **/add**.</span></span> <span data-ttu-id="2a59f-145">Supprime des listes de certificats de confiance si utilisée avec **/del**.</span><span class="sxs-lookup"><span data-stu-id="2a59f-145">Deletes CTLs when used with **/del**.</span></span> <span data-ttu-id="2a59f-146">Enregistre des listes de certificats de confiance si utilisée avec **/put**.</span><span class="sxs-lookup"><span data-stu-id="2a59f-146">Saves CTLs when used with **/put**.</span></span> <span data-ttu-id="2a59f-147">Affiche des listes de certificats de confiance si utilisée sans l'option **/add**, **/del** ou **/put**.</span><span class="sxs-lookup"><span data-stu-id="2a59f-147">Displays CTLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="2a59f-148">**/del**</span><span class="sxs-lookup"><span data-stu-id="2a59f-148">**/del**</span></span>|<span data-ttu-id="2a59f-149">Supprime des certificats, listes de certificats de confiance et listes de révocation de certificats dans un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="2a59f-149">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>|  
|<span data-ttu-id="2a59f-150">**/e** *type d’encodage*</span><span class="sxs-lookup"><span data-stu-id="2a59f-150">**/e** *encodingType*</span></span>|<span data-ttu-id="2a59f-151">Spécifie le type d'encodage des certificats.</span><span class="sxs-lookup"><span data-stu-id="2a59f-151">Specifies the certificate encoding type.</span></span> <span data-ttu-id="2a59f-152">La valeur par défaut est `X509_ASN_ENCODING`.</span><span class="sxs-lookup"><span data-stu-id="2a59f-152">The default is `X509_ASN_ENCODING`.</span></span>|  
|<span data-ttu-id="2a59f-153">**/f** *dwFlags*</span><span class="sxs-lookup"><span data-stu-id="2a59f-153">**/f** *dwFlags*</span></span>|<span data-ttu-id="2a59f-154">Spécifie l'indicateur d'ouverture du magasin.</span><span class="sxs-lookup"><span data-stu-id="2a59f-154">Specifies the store open flag.</span></span> <span data-ttu-id="2a59f-155">Il s'agit du paramètre *dwFlags* passé à **CertOpenStore**.</span><span class="sxs-lookup"><span data-stu-id="2a59f-155">This is the *dwFlags* parameter passed to **CertOpenStore**.</span></span> <span data-ttu-id="2a59f-156">Sa valeur par défaut est CERT_SYSTEM_STORE_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="2a59f-156">The default value is CERT_SYSTEM_STORE_CURRENT_USER.</span></span> <span data-ttu-id="2a59f-157">Cette option n'est prise en compte que si l'option **/y** est utilisée.</span><span class="sxs-lookup"><span data-stu-id="2a59f-157">This option is considered only if the **/y** option is used.</span></span>|  
|<span data-ttu-id="2a59f-158">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="2a59f-158">**/h**[**elp**]</span></span>|<span data-ttu-id="2a59f-159">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="2a59f-159">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="2a59f-160">**/n** *nam*</span><span class="sxs-lookup"><span data-stu-id="2a59f-160">**/n** *nam*</span></span>|<span data-ttu-id="2a59f-161">Spécifie le nom commun du certificat à ajouter, à supprimer ou à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="2a59f-161">Specifies the common name of the certificate to add, delete, or save.</span></span> <span data-ttu-id="2a59f-162">Cette option ne peut être utilisée qu'avec des certificats ; elle n'est pas compatible avec les listes de certificats de confiance, ni avec les listes de révocation de certificats.</span><span class="sxs-lookup"><span data-stu-id="2a59f-162">This option can only be used with certificates; it cannot be used with CTLs or CRLs.</span></span>|  
|<span data-ttu-id="2a59f-163">**/put**</span><span class="sxs-lookup"><span data-stu-id="2a59f-163">**/put**</span></span>|<span data-ttu-id="2a59f-164">Enregistre dans un fichier un certificat X.509, une liste de certificats de confiance ou une liste de révocation de certificats en provenance d'un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="2a59f-164">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span> <span data-ttu-id="2a59f-165">Le fichier est enregistré au format X.509.</span><span class="sxs-lookup"><span data-stu-id="2a59f-165">The file is saved in X.509 format.</span></span> <span data-ttu-id="2a59f-166">Vous pouvez utiliser l'option **/7** avec l'option **/put** pour enregistrer le fichier au format PKCS #7.</span><span class="sxs-lookup"><span data-stu-id="2a59f-166">You can use the **/7** option with the **/put** option to save the file in PKCS #7 format.</span></span> <span data-ttu-id="2a59f-167">L'option **/put** doit être suivie par **/c**, **/CTL** ou **/CRL**.</span><span class="sxs-lookup"><span data-stu-id="2a59f-167">The **/put** option must be followed by either **/c**, **/CTL**, or **/CRL**.</span></span> <span data-ttu-id="2a59f-168">L'option **/all** ne peut pas être utilisée avec **/put**.</span><span class="sxs-lookup"><span data-stu-id="2a59f-168">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="2a59f-169">**/r** *emplacement*</span><span class="sxs-lookup"><span data-stu-id="2a59f-169">**/r** *location*</span></span>|<span data-ttu-id="2a59f-170">Identifie l'emplacement du magasin système dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="2a59f-170">Identifies the registry location of the system store.</span></span> <span data-ttu-id="2a59f-171">Cette option n'est prise en compte que si l'option **/s** est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2a59f-171">This option is considered only if you specify the **/s** option.</span></span> <span data-ttu-id="2a59f-172">La valeur de *location* doit être l'une des suivantes :</span><span class="sxs-lookup"><span data-stu-id="2a59f-172">*location* must be one of the following:</span></span><br /><br /> <span data-ttu-id="2a59f-173">-   `currentUser` indique que le magasin de certificats se trouve sous la clé HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="2a59f-173">-   `currentUser` indicates that the certificate store is under the HKEY_CURRENT_USER key.</span></span> <span data-ttu-id="2a59f-174">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="2a59f-174">This is the default.</span></span><br /><span data-ttu-id="2a59f-175">-   `localMachine` indique que le magasin de certificats se trouve sous la clé HKEY_LOCAL_MACHINE.</span><span class="sxs-lookup"><span data-stu-id="2a59f-175">-   `localMachine` indicates that the certificate store is under the HKEY_LOCAL_MACHINE key.</span></span>|  
|<span data-ttu-id="2a59f-176">**/s**</span><span class="sxs-lookup"><span data-stu-id="2a59f-176">**/s**</span></span>|<span data-ttu-id="2a59f-177">Indique que le magasin de certificats est un magasin système.</span><span class="sxs-lookup"><span data-stu-id="2a59f-177">Indicates that the certificate store is a system store.</span></span> <span data-ttu-id="2a59f-178">Si vous ne spécifiez pas cette option, le magasin est considéré comme **StoreFile**.</span><span class="sxs-lookup"><span data-stu-id="2a59f-178">If you do not specify this option, the store is considered to be a **StoreFile**.</span></span>|  
|<span data-ttu-id="2a59f-179">**/sha1** *hachage sha1*</span><span class="sxs-lookup"><span data-stu-id="2a59f-179">**/sha1** *sha1Hash*</span></span>|<span data-ttu-id="2a59f-180">Spécifie le hachage SHA1 du certificat, de la liste de certificats de confiance ou de la liste de révocation de certificats à ajouter, à supprimer ou à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="2a59f-180">Specifies the SHA1 hash of the certificate, CTL, or CRL to add, delete, or save.</span></span>|  
|<span data-ttu-id="2a59f-181">**/v**</span><span class="sxs-lookup"><span data-stu-id="2a59f-181">**/v**</span></span>|<span data-ttu-id="2a59f-182">Spécifie le mode Commentaires ; affiche des informations détaillées sur les certificats, les listes de certificats de confiance et les listes de révocation de certificats.</span><span class="sxs-lookup"><span data-stu-id="2a59f-182">Specifies verbose mode; displays detailed information about certificates, CTLs, and CRLs.</span></span> <span data-ttu-id="2a59f-183">Vous ne pouvez pas utiliser cette option avec **/add**, **/del** ou **/put**.</span><span class="sxs-lookup"><span data-stu-id="2a59f-183">This option cannot be used with the **/add**, **/del**, or **/put** options.</span></span>|  
|<span data-ttu-id="2a59f-184">**/y** *fournisseur*</span><span class="sxs-lookup"><span data-stu-id="2a59f-184">**/y** *provider*</span></span>|<span data-ttu-id="2a59f-185">Spécifie le nom du fournisseur de magasin.</span><span class="sxs-lookup"><span data-stu-id="2a59f-185">Specifies the store provider name.</span></span>|  
|<span data-ttu-id="2a59f-186">**/7**</span><span class="sxs-lookup"><span data-stu-id="2a59f-186">**/7**</span></span>|<span data-ttu-id="2a59f-187">Enregistre le magasin de destination comme un objet PKCS #7.</span><span class="sxs-lookup"><span data-stu-id="2a59f-187">Saves the destination store as a PKCS #7 object.</span></span>|  
|<span data-ttu-id="2a59f-188">**/?**</span><span class="sxs-lookup"><span data-stu-id="2a59f-188">**/?**</span></span>|<span data-ttu-id="2a59f-189">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="2a59f-189">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a59f-190">Notes</span><span class="sxs-lookup"><span data-stu-id="2a59f-190">Remarks</span></span>  
 <span data-ttu-id="2a59f-191">Certmgr.exe exécute les fonctions de base suivantes :</span><span class="sxs-lookup"><span data-stu-id="2a59f-191">Certmgr.exe performs the following basic functions:</span></span>  
  
-   <span data-ttu-id="2a59f-192">Affiche les certificats, listes de certificats de confiance et listes de révocation de certificats dans la console.</span><span class="sxs-lookup"><span data-stu-id="2a59f-192">Displays certificates, CTLs, and CRLs to the console.</span></span>  
  
-   <span data-ttu-id="2a59f-193">Ajoute des certificats, listes de certificats de confiance et listes de révocation de certificats à un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="2a59f-193">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>  
  
-   <span data-ttu-id="2a59f-194">Supprime des certificats, listes de certificats de confiance et listes de révocation de certificats dans un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="2a59f-194">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>  
  
-   <span data-ttu-id="2a59f-195">Enregistre dans un fichier un certificat X.509, une liste de certificats de confiance ou une liste de révocation de certificats en provenance d'un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="2a59f-195">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span>  
  
 <span data-ttu-id="2a59f-196">Certmgr.exe fonctionne avec deux types de magasins de certificats : **StoreFile** et magasin système.</span><span class="sxs-lookup"><span data-stu-id="2a59f-196">Certmgr.exe works with two types of certificate stores: **StoreFile** and system store.</span></span> <span data-ttu-id="2a59f-197">Il n'est pas nécessaire de spécifier le type de magasin de certificats ; Certmgr.exe est capable de l'identifier et d'effectuer les opérations appropriées.</span><span class="sxs-lookup"><span data-stu-id="2a59f-197">It is not necessary to specify the type of certificate store; Certmgr.exe can identify the store type and perform the appropriate operations.</span></span>  
  
 <span data-ttu-id="2a59f-198">L'exécution de Certmgr.exe sans aucune option lance le composant logiciel enfichable certmgr.msc, qui dispose d'une interface utilisateur graphique (GUI) qui facilite les tâches de gestion des certificats qui sont également disponibles à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="2a59f-198">Running Certmgr.exe without specifying any options launches the certmgr.msc snap-in, which has a GUI that helps with the certificate management tasks that are also available from the command line.</span></span> <span data-ttu-id="2a59f-199">Cette interface utilisateur graphique fournit un Assistant d'importation qui copie les certificats, les listes de certificats de confiance et les listes de révocation de certificats depuis votre disque vers un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="2a59f-199">The GUI provides an import wizard, which copies certificates, CTLs, and CRLs from your disk to a certificate store.</span></span>  
  
 <span data-ttu-id="2a59f-200">Vous pouvez rechercher les noms de magasins de certificats X509 pour les paramètres `sourceStorename` et `destinationStorename` en compilant et en exécutant le code suivant.</span><span class="sxs-lookup"><span data-stu-id="2a59f-200">You can find the names of X509Certificate stores for the `sourceStorename` and `destinationStorename` parameters by compiling and running the following code.</span></span>  
  
 <span data-ttu-id="2a59f-201">[!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)] [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="2a59f-201">[!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)] [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]</span></span>  
  
 <span data-ttu-id="2a59f-202">Pour plus d’informations sur les certificats, consultez [Utilisation de certificats](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="2a59f-202">For more information about certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2a59f-203">Exemples</span><span class="sxs-lookup"><span data-stu-id="2a59f-203">Examples</span></span>  
 <span data-ttu-id="2a59f-204">La commande suivante affiche un magasin système par défaut appelé `my` avec une sortie des commentaires.</span><span class="sxs-lookup"><span data-stu-id="2a59f-204">The following command displays a default system store called `my` with verbose output.</span></span>  
  
```  
certmgr /v /s my  
```  
  
 <span data-ttu-id="2a59f-205">La commande suivante ajoute tous les certificats contenus dans un fichier nommé `myFile.ext` dans un nouveau fichier appelé `newFile.ext`.</span><span class="sxs-lookup"><span data-stu-id="2a59f-205">The following command adds all the certificates in a file called `myFile.ext` to a new file called `newFile.ext`.</span></span>  
  
```  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 <span data-ttu-id="2a59f-206">La commande suivante ajoute le certificat dans un fichier nommé `testcert.cer` au magasin système `my`.</span><span class="sxs-lookup"><span data-stu-id="2a59f-206">The following command adds the certificate in a file named `testcert.cer` to the `my` system store.</span></span>  
  
```  
certmgr /add /c testcert.cer /s my  
```  
  
 <span data-ttu-id="2a59f-207">La commande suivante ajoute le certificat dans un fichier nommé `TrustedCert.cer` dans le magasin de certificats racines.</span><span class="sxs-lookup"><span data-stu-id="2a59f-207">The following command adds the certificate in a file named `TrustedCert.cer` to the root certificate store.</span></span>  
  
```  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 <span data-ttu-id="2a59f-208">La commande suivante enregistre un certificat avec le nom commun `myCert` dans le magasin système `my` vers un fichier nommé `newCert.cer`.</span><span class="sxs-lookup"><span data-stu-id="2a59f-208">The following command saves a certificate with the common name `myCert` in the `my` system store to a file called `newCert.cer`.</span></span>  
  
```  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 <span data-ttu-id="2a59f-209">La commande suivante supprime toutes les listes de certificats de confiance du magasin système `my` et enregistre le magasin qui en résulte dans un fichier nommé `newStore.str`.</span><span class="sxs-lookup"><span data-stu-id="2a59f-209">The following command deletes all CTLs in the `my` system store and saves the resulting store to a file called `newStore.str`.</span></span>  
  
```  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 <span data-ttu-id="2a59f-210">La commande suivante enregistre un certificat dans le magasin système `my` du fichier `newFile`.</span><span class="sxs-lookup"><span data-stu-id="2a59f-210">The following command saves a certificate in the `my` system store in the file `newFile`.</span></span> <span data-ttu-id="2a59f-211">Vous devez saisir le numéro du certificat de `my` à placer dans `newFile`.</span><span class="sxs-lookup"><span data-stu-id="2a59f-211">You will be prompted to enter the certificate number from `my` to put in `newFile`.</span></span>  
  
```  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a59f-212">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a59f-212">See Also</span></span>  
 <span data-ttu-id="2a59f-213">[Outils](../../../docs/framework/tools/index.md) </span><span class="sxs-lookup"><span data-stu-id="2a59f-213">[Tools](../../../docs/framework/tools/index.md) </span></span>  
 <span data-ttu-id="2a59f-214">[Makecert.exe (outil de la création du certificat)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) </span><span class="sxs-lookup"><span data-stu-id="2a59f-214">[Makecert.exe (Certificate Creation Tool)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) </span></span>  
 [<span data-ttu-id="2a59f-215">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="2a59f-215">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

