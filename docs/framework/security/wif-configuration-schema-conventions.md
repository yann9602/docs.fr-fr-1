---
title: "Conventions de schéma de configuration de WIF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: e327b45ddd260d1a52066b5bf53e7114100ff45c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="wif-configuration-schema-conventions"></a><span data-ttu-id="2db96-102">Conventions de schéma de configuration de WIF</span><span class="sxs-lookup"><span data-stu-id="2db96-102">WIF Configuration Schema Conventions</span></span>
<span data-ttu-id="2db96-103">Cette rubrique explique les conventions employées dans les rubriques traitant de la configuration de WIF (Windows Identity Foundation). Elle décrit également certaines fonctionnalités et attributs souvent utilisés dans les sections [\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) et [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md).</span><span class="sxs-lookup"><span data-stu-id="2db96-103">This topic discusses conventions used throughout the Windows Identity Foundation (WIF) configuration topics and describes some common features and attributes used in the [\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) and the [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) sections.</span></span>  
  
<a name="BKMK_Modes"></a>   
## <a name="modes"></a><span data-ttu-id="2db96-104">Modes</span><span class="sxs-lookup"><span data-stu-id="2db96-104">Modes</span></span>  
 <span data-ttu-id="2db96-105">La plupart des éléments de configuration de WIF ont un attribut `mode`.</span><span class="sxs-lookup"><span data-stu-id="2db96-105">Many of the WIF configuration elements have a `mode` attribute.</span></span> <span data-ttu-id="2db96-106">Cet attribut détermine généralement la classe à utiliser pour effectuer certaines tâches du traitement, ainsi que les éléments de configuration qui peuvent être utilisés comme éléments enfants de l’élément actuel.</span><span class="sxs-lookup"><span data-stu-id="2db96-106">This attribute typically controls which class is used to do a particular part of the processing and which configuration elements are allowed as child elements of the current element.</span></span> <span data-ttu-id="2db96-107">Une erreur de configuration se produit si des éléments inclus dans le fichier de configuration sont ignorés en raison des paramètres de mode définis.</span><span class="sxs-lookup"><span data-stu-id="2db96-107">A configuration error will be raised if elements that are included in the configuration file are ignored because of the mode settings.</span></span>  
  
<a name="BKMK_TimespanValues"></a>   
## <a name="timespan-values"></a><span data-ttu-id="2db96-108">Valeurs Timespan</span><span class="sxs-lookup"><span data-stu-id="2db96-108">Timespan Values</span></span>  
 <span data-ttu-id="2db96-109">Si <xref:System.TimeSpan> est utilisé comme type d’attribut, consultez la méthode <xref:System.TimeSpan.Parse%28System.String%29> pour connaître le format autorisé.</span><span class="sxs-lookup"><span data-stu-id="2db96-109">Where <xref:System.TimeSpan> is used as the type of an attribute, see the <xref:System.TimeSpan.Parse%28System.String%29> method to see the allowed format.</span></span> <span data-ttu-id="2db96-110">Ce format respecte la spécification suivante.</span><span class="sxs-lookup"><span data-stu-id="2db96-110">This format conforms to the following specification.</span></span>  
  
```  
[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]  
```  
  
 <span data-ttu-id="2db96-111">Par exemple, les valeurs « 30 », « 30.00:00 » et « 30.00:00:00 » représentent toutes une durée de 30 jours, et les valeurs « 00:05 », « 00:05:00 » et « 0.00:05:00.00 » représentent toutes une durée de 5 minutes.</span><span class="sxs-lookup"><span data-stu-id="2db96-111">For example, "30", "30.00:00", "30.00:00:00" all mean 30 days; and "00:05", "00:05:00", "0.00:05:00.00" all mean 5 minutes.</span></span>  
  
<a name="BKMK_CertificateReferences"></a>   
## <a name="certificate-references"></a><span data-ttu-id="2db96-112">Références à des certificats</span><span class="sxs-lookup"><span data-stu-id="2db96-112">Certificate References</span></span>  
 <span data-ttu-id="2db96-113">Plusieurs éléments font référence à des certificats à l’aide de l’élément `<certificateReference>`.</span><span class="sxs-lookup"><span data-stu-id="2db96-113">Several elements take references to certificates using the `<certificateReference>` element.</span></span> <span data-ttu-id="2db96-114">Pour faire référence à un certificat, vous pouvez utiliser les attributs suivants.</span><span class="sxs-lookup"><span data-stu-id="2db96-114">When referencing a certificate, the following attributes are available.</span></span>  
  
|||  
|-|-|  
|`storeLocation`|<span data-ttu-id="2db96-115">Une valeur de l’énumération <xref:System.Security.Cryptography.X509Certificates.StoreLocation> : `CurrentUser` ou `CurrentMachine`.</span><span class="sxs-lookup"><span data-stu-id="2db96-115">A value of the <xref:System.Security.Cryptography.X509Certificates.StoreLocation> enumeration: `CurrentUser` or `CurrentMachine`.</span></span>|  
|`storeName`|<span data-ttu-id="2db96-116">Une valeur de l’énumération <xref:System.Security.Cryptography.X509Certificates.StoreName>. Les valeurs `My` et `TrustedPeople` sont les plus utiles dans ce contexte.</span><span class="sxs-lookup"><span data-stu-id="2db96-116">A value of the <xref:System.Security.Cryptography.X509Certificates.StoreName> enumeration; the most useful for this context are `My` and `TrustedPeople`.</span></span>|  
|`x509FindType`|<span data-ttu-id="2db96-117">Une valeur de l’énumération <xref:System.Security.Cryptography.X509Certificates.X509FindType>. Les valeurs `FindBySubjectName` et `FindByThumbprint` sont les plus utiles dans ce contexte.</span><span class="sxs-lookup"><span data-stu-id="2db96-117">A value of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> enumeration; the most useful for this context are `FindBySubjectName` and `FindByThumbprint`.</span></span> <span data-ttu-id="2db96-118">Pour éliminer le risque d’erreur, il est recommandé d’utiliser le type `FindByThumbprint` dans les environnements de production.</span><span class="sxs-lookup"><span data-stu-id="2db96-118">To eliminate the chance of error, it is recommended that the `FindByThumbprint` type be used in production environments.</span></span>|  
|`findValue`|<span data-ttu-id="2db96-119">La valeur utilisée pour rechercher le certificat sur la base de l’attribut `x509FindType`.</span><span class="sxs-lookup"><span data-stu-id="2db96-119">The value used to find the certificate, based on the `x509FindType` attribute.</span></span> <span data-ttu-id="2db96-120">Pour éliminer le risque d’erreur, il est recommandé d’utiliser le type `FindByThumbprint` dans les environnements de production.</span><span class="sxs-lookup"><span data-stu-id="2db96-120">To eliminate the chance of error, it is recommended that the `FindByThumbprint` type be used in production environments.</span></span> <span data-ttu-id="2db96-121">Quand `FindByThumbPrint` est spécifié, cet attribut a une valeur représentant l’empreinte numérique du certificat au format de chaîne hexadécimale. Par exemple, « 97249e1a5fa6bee5e515b82111ef524a4c91583f ».</span><span class="sxs-lookup"><span data-stu-id="2db96-121">When `FindByThumbPrint` is specified, this attribute takes a value that is the hexadecimal-string form of the certificate thumbprint; for example, "97249e1a5fa6bee5e515b82111ef524a4c91583f".</span></span>|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## <a name="custom-type-references"></a><span data-ttu-id="2db96-122">Références à des types personnalisés</span><span class="sxs-lookup"><span data-stu-id="2db96-122">Custom Type References</span></span>  
 <span data-ttu-id="2db96-123">Plusieurs éléments peuvent faire référence à des types personnalisés à l’aide de l’attribut `type`.</span><span class="sxs-lookup"><span data-stu-id="2db96-123">Several elements reference custom types using the `type` attribute.</span></span> <span data-ttu-id="2db96-124">Cet attribut doit spécifier le nom du type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2db96-124">This attribute should specify the name of the custom type.</span></span> <span data-ttu-id="2db96-125">Pour faire référence à un type à partir du Global Assembly Cache (GAC), utilisez un nom fort.</span><span class="sxs-lookup"><span data-stu-id="2db96-125">To reference a type from the Global Assembly Cache (GAC), a strong name should be used.</span></span> <span data-ttu-id="2db96-126">Pour faire référence à un type à partir d’un assembly du répertoire Bin/, utilisez une référence qualifiée d’assembly simple.</span><span class="sxs-lookup"><span data-stu-id="2db96-126">To reference a type from an assembly in the Bin/ directory, a simple assembly-qualified reference may be used.</span></span> <span data-ttu-id="2db96-127">Les types définis dans le répertoire App_Code/ peuvent également être référencés simplement par le nom de type, sans référence d’assembly qualifiée.</span><span class="sxs-lookup"><span data-stu-id="2db96-127">Types defined in the App_Code/ directory may also be referenced by simply specifying the type name with no qualifying assembly.</span></span>  
  
 <span data-ttu-id="2db96-128">Les types personnalisés doivent être dérivés du type spécifié et fournir un constructeur `public` par défaut (sans argument).</span><span class="sxs-lookup"><span data-stu-id="2db96-128">Custom types must be derived from the type specified and they must provide a `public` default (0 argument) constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2db96-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2db96-129">See Also</span></span>  
 [<span data-ttu-id="2db96-130">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="2db96-130">\<system.identityModel></span></span>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)  
 [<span data-ttu-id="2db96-131">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="2db96-131">\<system.identityModel.services></span></span>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)
