---
title: "Atténuation : Séparateur de chemin ZipArchiveEntry.FullName"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c9f271e10014d2f6fb04eb4279b068b7a191639f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="fe1ad-102">Atténuation : Séparateur de chemin ZipArchiveEntry.FullName</span><span class="sxs-lookup"><span data-stu-id="fe1ad-102">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>
<span data-ttu-id="fe1ad-103">À compter des applications qui ciblent le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], le séparateur de chemin utilisé dans la propriété <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=fullName> a été changé. Il ne s’agit plus de la barre oblique inverse (« \\ ») utilisée dans les versions antérieures du .NET Framework, mais de la barre oblique (« / »).</span><span class="sxs-lookup"><span data-stu-id="fe1ad-103">Starting with apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=fullName> property has changed from the backslash ("\\") used in previous versions of the .NET Framework to a forward slash ("/").</span></span>   <span data-ttu-id="fe1ad-104">Les objets <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=fullName> sont créés en appelant l’une des surcharges de la méthode <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="fe1ad-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=fullName> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=fullName> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="fe1ad-105">Impact</span><span class="sxs-lookup"><span data-stu-id="fe1ad-105">Impact</span></span>  
 <span data-ttu-id="fe1ad-106">L’implémentation .NET est ainsi conforme à la section 4.4.17.1 des [Spécifications relatives au format des fichiers ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) et permet aux archives ZIP d’être décompressées sur des systèmes non Windows.</span><span class="sxs-lookup"><span data-stu-id="fe1ad-106">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="fe1ad-107">Décompresser un fichier zip créé par une application qui cible une version antérieure de .NET Framework sur les systèmes d’exploitation non Windows tels que les ordinateurs Macintosh ne permet pas de conserver la structure de répertoire.</span><span class="sxs-lookup"><span data-stu-id="fe1ad-107">Decompressing a zip file created  by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="fe1ad-108">Par exemple, pour les ordinateurs Macintosh, cela crée un ensemble de fichiers dont le nom concatène le chemin d’accès, ainsi que toute barre oblique inverse (« \\ ») et le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="fe1ad-108">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="fe1ad-109">Par conséquent, la structure de répertoires des fichiers décompressés n’est pas conservée.</span><span class="sxs-lookup"><span data-stu-id="fe1ad-109">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="fe1ad-110">L’impact de ce changement sur les fichiers .ZIP qui sont décompressés sur le système d’exploitation Windows par les API dans l’espace de noms <xref:System.IO> du .NET Framework doit être minimal, étant donné que ces API peuvent gérer sans problème aussi bien une barre oblique (« / ») qu’une barre oblique inverse (« \\ ») comme séparateur de chemin.</span><span class="sxs-lookup"><span data-stu-id="fe1ad-110">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="fe1ad-111">Atténuation</span><span class="sxs-lookup"><span data-stu-id="fe1ad-111">Mitigation</span></span>  
 <span data-ttu-id="fe1ad-112">Si ce comportement n’est pas souhaitable, vous pouvez choisir de l’annuler en ajoutant un paramètre de configuration pour la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de votre application.</span><span class="sxs-lookup"><span data-stu-id="fe1ad-112">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="fe1ad-113">L’exemple suivant montre la section `<runtime>` et l’option d’annulation.</span><span class="sxs-lookup"><span data-stu-id="fe1ad-113">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="fe1ad-114">De plus, les applications qui ciblent des versions antérieures du .NET Framework, mais qui s’exécutent sur le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ou ultérieur peuvent adhérer à ce comportement en ajoutant un paramètre de configuration dans la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="fe1ad-114">In addition, apps that target previous versions of the .NET Framework but are running on the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="fe1ad-115">L’exemple suivant montre la section `<runtime>` et l’option d’activation.</span><span class="sxs-lookup"><span data-stu-id="fe1ad-115">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe1ad-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe1ad-116">See Also</span></span>  
 <span data-ttu-id="fe1ad-117">[Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md) </span><span class="sxs-lookup"><span data-stu-id="fe1ad-117">[Retargeting Changes](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md) </span></span>  
 [<span data-ttu-id="fe1ad-118">Compatibilité des applications dans la version 4.6.1</span><span class="sxs-lookup"><span data-stu-id="fe1ad-118">Application Compatibility in 4.6.1</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)

