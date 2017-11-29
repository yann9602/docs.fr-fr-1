---
title: "Spécification d’un Assembly &#39; s emplacement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f747d921e9c131edaa8a1749c5adc5eae14623c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="specifying-an-assembly39s-location"></a><span data-ttu-id="ae92a-102">Spécification d’un Assembly &#39; s emplacement</span><span class="sxs-lookup"><span data-stu-id="ae92a-102">Specifying an Assembly&#39;s Location</span></span>
<span data-ttu-id="ae92a-103">Il existe deux façons de spécifier l’emplacement d’un assembly :</span><span class="sxs-lookup"><span data-stu-id="ae92a-103">There are two ways to specify an assembly's location:</span></span>  
  
-   <span data-ttu-id="ae92a-104">À l’aide de la [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="ae92a-104">Using the [\<codeBase>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element.</span></span>  
  
-   <span data-ttu-id="ae92a-105">À l’aide de la [ \<probing >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="ae92a-105">Using the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="ae92a-106">Vous pouvez également utiliser le [.NET Framework Configuration Tool (Mscorcfg.msc)](http://msdn.microsoft.com/en-us/a7106c52-68da-490e-b129-971b2c743764) pour spécifier les emplacements des assemblys ou des emplacements pour le common language runtime détecter les assemblys.</span><span class="sxs-lookup"><span data-stu-id="ae92a-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](http://msdn.microsoft.com/en-us/a7106c52-68da-490e-b129-971b2c743764) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="ae92a-107">À l’aide de la \<codeBase > élément</span><span class="sxs-lookup"><span data-stu-id="ae92a-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="ae92a-108">Vous pouvez utiliser la  **\<codeBase >** élément uniquement dans l’ordinateur serveur de publication stratégie fichiers de configuration ou qui redirigent également la version d’assembly.</span><span class="sxs-lookup"><span data-stu-id="ae92a-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="ae92a-109">Lorsque le runtime détermine la version d’assembly à utiliser, il applique le paramètre de base de code à partir du fichier qui détermine la version.</span><span class="sxs-lookup"><span data-stu-id="ae92a-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="ae92a-110">Si aucune base de code n’est indiqué, le runtime tente de détecter l’assembly de façon normale.</span><span class="sxs-lookup"><span data-stu-id="ae92a-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="ae92a-111">Pour plus d’informations, consultez [méthode de localisation des assemblys par le Runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="ae92a-111">For details, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="ae92a-112">L’exemple suivant montre comment spécifier l’emplacement d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="ae92a-112">The following example shows how to specify an assembly's location.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <codeBase version="2.0.0.0"  
                   href="http://www.litwareinc.com/myAssembly.dll"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="ae92a-113">Le **version** attribut est requis pour tous les assemblys avec nom fort, mais doit être omis pour les assemblys qui ne sont pas de nom fort.</span><span class="sxs-lookup"><span data-stu-id="ae92a-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="ae92a-114">Le  **\<codeBase >** élément requiert le **href** attribut.</span><span class="sxs-lookup"><span data-stu-id="ae92a-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="ae92a-115">Vous ne pouvez pas spécifier les plages de versions dans le  **\<codeBase >** élément.</span><span class="sxs-lookup"><span data-stu-id="ae92a-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae92a-116">Si vous fournissez un indicateur de base de code pour un assembly qui n’est pas de nom fort, l’indicateur doit pointer vers la base de l’application ou un sous-répertoire du répertoire de base de l’application.</span><span class="sxs-lookup"><span data-stu-id="ae92a-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="ae92a-117">À l’aide de la \<probing > élément</span><span class="sxs-lookup"><span data-stu-id="ae92a-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="ae92a-118">Le runtime localise les assemblys qui n’ont pas d’une base de code par la détection.</span><span class="sxs-lookup"><span data-stu-id="ae92a-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="ae92a-119">Pour plus d’informations sur la détection, consultez [méthode de localisation des assemblys par le Runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="ae92a-119">For more information about probing, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="ae92a-120">Vous pouvez utiliser la [ \<probing >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) élément dans le fichier de configuration d’application pour spécifier les sous-répertoires dans lesquels le runtime doit rechercher lors de la localisation d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="ae92a-120">You can use the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="ae92a-121">L’exemple suivant montre comment spécifier le runtime doit rechercher les répertoires.</span><span class="sxs-lookup"><span data-stu-id="ae92a-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="ae92a-122">Le **privatePath** attribut contient les répertoires dans lesquels le runtime doit rechercher les assemblys.</span><span class="sxs-lookup"><span data-stu-id="ae92a-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="ae92a-123">Si l’application se trouve dans C:\Program Files\MyApp, le runtime recherche les assemblys qui ne spécifient pas une base de code dans C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin et C:\Program Files\MyApp\Bin3.</span><span class="sxs-lookup"><span data-stu-id="ae92a-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="ae92a-124">Les répertoires spécifiés dans **privatePath** doivent être des sous-répertoires du répertoire de base de l’application.</span><span class="sxs-lookup"><span data-stu-id="ae92a-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae92a-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae92a-125">See Also</span></span>  
 [<span data-ttu-id="ae92a-126">Assemblys dans le Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="ae92a-126">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [<span data-ttu-id="ae92a-127">Programmation à l’aide d’assemblys</span><span class="sxs-lookup"><span data-stu-id="ae92a-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="ae92a-128">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="ae92a-128">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="ae92a-129">Configuration des applications .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ae92a-129">Configuring .NET Framework Apps</span></span>](http://msdn.microsoft.com/en-us/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
