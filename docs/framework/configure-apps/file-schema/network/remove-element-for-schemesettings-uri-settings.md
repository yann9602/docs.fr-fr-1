---
title: "&lt;Supprimez&gt; , élément de schemeSettings (paramètres d’Uri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6d587dced4660774b67a8e884bf6c25df3b6e400
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltremovegt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="ba214-102">&lt;Supprimez&gt; , élément de schemeSettings (paramètres d’Uri)</span><span class="sxs-lookup"><span data-stu-id="ba214-102">&lt;remove&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="ba214-103">Supprime un paramètre de schéma pour un nom de schéma.</span><span class="sxs-lookup"><span data-stu-id="ba214-103">Removes a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="ba214-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ba214-104">\<configuration></span></span>  
<span data-ttu-id="ba214-105">\<URI ></span><span class="sxs-lookup"><span data-stu-id="ba214-105">\<uri></span></span>  
<span data-ttu-id="ba214-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="ba214-106">\<schemeSettings></span></span>  
<span data-ttu-id="ba214-107">\<Supprimer ></span><span class="sxs-lookup"><span data-stu-id="ba214-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba214-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba214-108">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba214-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ba214-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ba214-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ba214-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba214-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="ba214-111">Attributes</span></span>  
  
|<span data-ttu-id="ba214-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="ba214-112">Attribute</span></span>|<span data-ttu-id="ba214-113">Description</span><span class="sxs-lookup"><span data-stu-id="ba214-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ba214-114">name</span><span class="sxs-lookup"><span data-stu-id="ba214-114">name</span></span>|<span data-ttu-id="ba214-115">Le nom du schéma auquel ce paramètre s’applique.</span><span class="sxs-lookup"><span data-stu-id="ba214-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="ba214-116">Les seules valeurs prises en charge sont nom = « http » et le nom = « https ».</span><span class="sxs-lookup"><span data-stu-id="ba214-116">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ba214-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ba214-117">Child Elements</span></span>  
 <span data-ttu-id="ba214-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ba214-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ba214-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ba214-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ba214-120">Élément</span><span class="sxs-lookup"><span data-stu-id="ba214-120">Element</span></span>|<span data-ttu-id="ba214-121">Description</span><span class="sxs-lookup"><span data-stu-id="ba214-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba214-122">\<schemeSettings, élément (paramètres d’Uri)</span><span class="sxs-lookup"><span data-stu-id="ba214-122">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="ba214-123">Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.</span><span class="sxs-lookup"><span data-stu-id="ba214-123">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba214-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="ba214-124">Remarks</span></span>  
 <span data-ttu-id="ba214-125">Par défaut, le <xref:System.Uri?displayProperty=nameWithType> pour cent de classe n’échappe pas encodée séparateurs de chemin d’accès avant d’exécuter la compression de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="ba214-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="ba214-126">Cela a été implémenté en tant que mécanisme de sécurité contre les attaques comme suit :</span><span class="sxs-lookup"><span data-stu-id="ba214-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="ba214-127">Si cet URI est passé à des modules ne gère ne pas % correctement les caractères encodés, elle peut entraîner la commande suivante, exécutée par le serveur :</span><span class="sxs-lookup"><span data-stu-id="ba214-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="ba214-128">Pour cette raison, <xref:System.Uri?displayProperty=nameWithType> première séparateurs de chemin d’accès n’échappe pas de classe, puis applique la compression de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="ba214-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="ba214-129">Le résultat du passage de l’URL malveillante ci-dessus pour <xref:System.Uri?displayProperty=nameWithType> classe constructeur se traduit par l’URI suivant :</span><span class="sxs-lookup"><span data-stu-id="ba214-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="ba214-130">Ce comportement par défaut peut être modifié pour ne pas les délimiteurs de chemin d’accès codé en pourcentage échapper à l’aide de l’option de configuration schemeSettings pour un modèle spécifique.</span><span class="sxs-lookup"><span data-stu-id="ba214-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ba214-131">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="ba214-131">Configuration Files</span></span>  
 <span data-ttu-id="ba214-132">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="ba214-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba214-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="ba214-133">Example</span></span>  
 <span data-ttu-id="ba214-134">L’exemple suivant montre une configuration utilisée par la <xref:System.Uri> classe qui supprime les paramètres de schéma pour le schéma http.</span><span class="sxs-lookup"><span data-stu-id="ba214-134">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba214-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba214-135">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="ba214-136">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="ba214-136">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
