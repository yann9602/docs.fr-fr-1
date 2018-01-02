---
title: "&lt;useLegacyJit&gt; élément"
ms.custom: 
ms.date: 04/26/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d2a71e44db2d6e85ae730f4603bf191f54525c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltuselegacyjitgt-element"></a><span data-ttu-id="66029-102">&lt;useLegacyJit&gt; élément</span><span class="sxs-lookup"><span data-stu-id="66029-102">&lt;useLegacyJit&gt; Element</span></span>

<span data-ttu-id="66029-103">Détermine si le common language runtime utilise le compilateur JIT 64 bits hérité pour la compilation juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="66029-103">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
<span data-ttu-id="66029-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="66029-104">\<configuration></span></span>  
<span data-ttu-id="66029-105">\<runtime ></span><span class="sxs-lookup"><span data-stu-id="66029-105">\<runtime></span></span>  
<span data-ttu-id="66029-106">\<useLegacyJit ></span><span class="sxs-lookup"><span data-stu-id="66029-106">\<useLegacyJit></span></span>
  
## <a name="syntax"></a><span data-ttu-id="66029-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66029-107">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="66029-108">Nom de l’élément `useLegacyJit` respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="66029-108">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66029-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="66029-109">Attributes and elements</span></span>

<span data-ttu-id="66029-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="66029-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66029-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="66029-111">Attributes</span></span>  
  
| <span data-ttu-id="66029-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="66029-112">Attribute</span></span> | <span data-ttu-id="66029-113">Description</span><span class="sxs-lookup"><span data-stu-id="66029-113">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="66029-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="66029-114">Required attribute.</span></span><br><br><span data-ttu-id="66029-115">Spécifie si le runtime utilise le compilateur JIT 64 bits hérité.</span><span class="sxs-lookup"><span data-stu-id="66029-115">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="66029-116">attribut Enabled</span><span class="sxs-lookup"><span data-stu-id="66029-116">enabled attribute</span></span>  
  
| <span data-ttu-id="66029-117">Value</span><span class="sxs-lookup"><span data-stu-id="66029-117">Value</span></span> | <span data-ttu-id="66029-118">Description</span><span class="sxs-lookup"><span data-stu-id="66029-118">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="66029-119">0</span><span class="sxs-lookup"><span data-stu-id="66029-119">0</span></span>     | <span data-ttu-id="66029-120">Le common language runtime utilise le nouveau compilateur JIT 64 bits inclus dans le .NET Framework 4.6 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="66029-120">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="66029-121">1</span><span class="sxs-lookup"><span data-stu-id="66029-121">1</span></span>     | <span data-ttu-id="66029-122">Le common language runtime utilise le compilateur JIT 64 bits plus anciens.</span><span class="sxs-lookup"><span data-stu-id="66029-122">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="66029-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="66029-123">Child elements</span></span>

<span data-ttu-id="66029-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="66029-124">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="66029-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="66029-125">Parent elements</span></span>  
  
| <span data-ttu-id="66029-126">Élément</span><span class="sxs-lookup"><span data-stu-id="66029-126">Element</span></span>         | <span data-ttu-id="66029-127">Description</span><span class="sxs-lookup"><span data-stu-id="66029-127">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="66029-128">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="66029-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="66029-129">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="66029-129">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="66029-130">Notes</span><span class="sxs-lookup"><span data-stu-id="66029-130">Remarks</span></span>  

<span data-ttu-id="66029-131">À compter de .NET Framework 4.6, le common language runtime utilise un nouveau compilateur 64 bits pour la compilation juste à temps (JIT) par défaut.</span><span class="sxs-lookup"><span data-stu-id="66029-131">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="66029-132">Dans certains cas, cela peut entraîner une différence de comportement du code d’application qui a été compilé juste-à la version précédente du compilateur JIT 64 bits.</span><span class="sxs-lookup"><span data-stu-id="66029-132">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="66029-133">En définissant le `enabled` attribut de la `<useLegacyJit>` élément `1`, vous pouvez désactiver le nouveau compilateur JIT 64 bits et à la place compiler votre application à l’aide du compilateur JIT 64 bits hérité.</span><span class="sxs-lookup"><span data-stu-id="66029-133">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="66029-134">Le `<useLegacyJit>` élément affecte uniquement la compilation JIT 64 bits.</span><span class="sxs-lookup"><span data-stu-id="66029-134">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="66029-135">Compilation avec le compilateur JIT 32 bits n’est pas affectée.</span><span class="sxs-lookup"><span data-stu-id="66029-135">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="66029-136">Au lieu d’utiliser une fichier de configuration, vous pouvez activer le compilateur JIT 64 bits hérité de deux manières différentes :</span><span class="sxs-lookup"><span data-stu-id="66029-136">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="66029-137">Définition d’une variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="66029-137">Setting an environment variable</span></span>

  <span data-ttu-id="66029-138">Définir le `COMPLUS_useLegacyJit` variable d’environnement soit `0` (utiliser le nouveau compilateur JIT 64 bits) ou `1` (utiliser le compilateur JIT 64 bits plus anciens) :</span><span class="sxs-lookup"><span data-stu-id="66029-138">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="66029-139">La variable d’environnement a *étendue globale*, ce qui signifie qu’il affecte toutes les applications s’exécutent sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="66029-139">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="66029-140">Si la valeur, elle peut être substituée par le paramètre fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="66029-140">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="66029-141">Le nom de variable d’environnement ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="66029-141">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="66029-142">Ajout d’une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="66029-142">Adding a registry key</span></span>

  <span data-ttu-id="66029-143">Vous pouvez activer le compilateur JIT 64 bits hérité en ajoutant un `REG_DWORD` valeur soit la `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` ou `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` clé dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="66029-143">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="66029-144">La valeur est nommée `useLegacyJit`.</span><span class="sxs-lookup"><span data-stu-id="66029-144">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="66029-145">Si la valeur est 0, le nouveau compilateur est utilisé.</span><span class="sxs-lookup"><span data-stu-id="66029-145">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="66029-146">Si la valeur est 1, le compilateur JIT 64 bits hérité est activé.</span><span class="sxs-lookup"><span data-stu-id="66029-146">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="66029-147">Le nom de la valeur du Registre n’est pas sensible à la casse.</span><span class="sxs-lookup"><span data-stu-id="66029-147">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="66029-148">Ajout de la valeur pour le `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` clé affecte toutes les applications en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="66029-148">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="66029-149">Ajout de la valeur pour le `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` clé affecte toutes les applications exécutées par l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="66029-149">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="66029-150">Si un ordinateur est configuré avec plusieurs comptes d’utilisateur, seules les applications exécutées par l’utilisateur actuel sont affectées, sauf si la valeur est ajoutée aux clés de Registre pour d’autres utilisateurs ainsi.</span><span class="sxs-lookup"><span data-stu-id="66029-150">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="66029-151">Ajout de la `<useLegacyJit>` élément vers un fichier de configuration remplace les paramètres du Registre, s’ils sont présents.</span><span class="sxs-lookup"><span data-stu-id="66029-151">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66029-152">Exemple</span><span class="sxs-lookup"><span data-stu-id="66029-152">Example</span></span>  

<span data-ttu-id="66029-153">Le fichier de configuration suivant désactive la compilation avec le nouveau compilateur JIT 64 bits et utilise à la place le compilateur JIT 64 bits hérité.</span><span class="sxs-lookup"><span data-stu-id="66029-153">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="66029-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66029-154">See also</span></span>

<span data-ttu-id="66029-155">[\<runtime > élément](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="66029-155">[\<runtime> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) </span></span>  
<span data-ttu-id="66029-156">[\<configuration > élément](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="66029-156">[\<configuration> Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
[<span data-ttu-id="66029-157">Atténuation : nouveau compilateur JIT 64 bits</span><span class="sxs-lookup"><span data-stu-id="66029-157">Mitigation: New 64-bit JIT Compiler</span></span>](../../../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md)
