---
title: "Création de prototypes dans du code managé"
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
- cpp
helpviewer_keywords:
- prototypes in managed code
- COM interop, DLL functions
- unmanaged functions
- platform invoke, creating prototypes
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, object fields
- DLL functions
- object fields in platform invoke
ms.assetid: ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d1006f59f9841a10066c83a8f0800d3a7c17500a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="creating-prototypes-in-managed-code"></a><span data-ttu-id="f2bc0-102">Création de prototypes dans du code managé</span><span class="sxs-lookup"><span data-stu-id="f2bc0-102">Creating Prototypes in Managed Code</span></span>
<span data-ttu-id="f2bc0-103">Cette rubrique décrit comment accéder aux fonctions non managées et présente plusieurs champs d’attribut qui permettent d’annoter les définitions de méthode dans du code managé.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-103">This topic describes how to access unmanaged functions and introduces several attribute fields that annotate method definition in managed code.</span></span> <span data-ttu-id="f2bc0-104">Pour afficher des exemples montrant comment construire des déclarations .NET à utiliser avec l’appel de code non managé, consultez [Marshaling de données à l’aide de l’appel de code non managé](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="f2bc0-104">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
 <span data-ttu-id="f2bc0-105">Avant de pouvoir accéder à une fonction DLL non managée depuis du code managé, vous devez connaître le nom de la fonction et le nom de la DLL qui l'exporte.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-105">Before you can access an unmanaged DLL function from managed code, you need to know the name of the function and the name of the DLL that exports it.</span></span> <span data-ttu-id="f2bc0-106">Avec ces informations, vous pouvez commencer à écrire la définition managée d'une fonction non managée implémentée dans une DLL.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-106">With this information, you can begin to write the managed definition for an unmanaged function that is implemented in a DLL.</span></span> <span data-ttu-id="f2bc0-107">En outre, vous pouvez ajuster la façon dont l'appel de code non managé crée la fonction et marshale les données vers et depuis la fonction.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-107">Furthermore, you can adjust the way that platform invoke creates the function and marshals data to and from the function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2bc0-108">Les fonctions de l'API Win32 qui allouent une chaîne vous permettent de libérer la chaîne à l'aide d'une méthode telle que `LocalFree`.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-108">Win32 API functions that allocate a string enable you to free the string by using a method such as `LocalFree`.</span></span> <span data-ttu-id="f2bc0-109">L'appel de code non managé gère ces paramètres différemment.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-109">Platform invoke handles such parameters differently.</span></span> <span data-ttu-id="f2bc0-110">Pour les appels de code non managé, affectez au paramètre un type `IntPtr` au lieu d'un type `String`.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-110">For platform invoke calls, make the parameter an `IntPtr` type instead of a `String` type.</span></span> <span data-ttu-id="f2bc0-111">Utilisez les méthodes fournies par la classe <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> pour convertir manuellement le type en chaîne et le libérer manuellement.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-111">Use methods that are provided by the <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> class to convert the type to a string manually and free it manually.</span></span>  
  
## <a name="declaration-basics"></a><span data-ttu-id="f2bc0-112">Principes de base des déclarations</span><span class="sxs-lookup"><span data-stu-id="f2bc0-112">Declaration Basics</span></span>  
 <span data-ttu-id="f2bc0-113">Les définitions managées des fonctions non managées dépendent du langage, comme nous allons le voir dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-113">Managed definitions to unmanaged functions are language-dependent, as you can see in the following examples.</span></span> <span data-ttu-id="f2bc0-114">Pour obtenir des exemples de code plus complets, consultez [Exemples d’appel de code non managé](../../../docs/framework/interop/platform-invoke-examples.md).</span><span class="sxs-lookup"><span data-stu-id="f2bc0-114">For more complete code examples, see [Platform Invoke Examples](../../../docs/framework/interop/platform-invoke-examples.md).</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, _  
        ByVal txt As String, ByVal caption As String, _  
        ByVal Typ As Integer) As IntPtr  
End Class  
```  
  
 <span data-ttu-id="f2bc0-115">Pour appliquer les champs <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> ou <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar> à une déclaration [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], vous devez utiliser l'attribut <xref:System.Runtime.InteropServices.DllImportAttribute> au lieu de l'instruction `Declare`.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-115">To apply the <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>, or <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar> fields to a [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] declaration, you must use the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute instead of the `Declare` statement.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
Public Class Win32  
   <DllImport ("user32.dll", CharSet := CharSet.Auto)> _  
   Public Shared Function MessageBox (ByVal hWnd As Integer, _  
        ByVal txt As String, ByVal caption As String, _  
        ByVal Typ As Integer) As IntPtr  
   End Function  
End Class  
```  
  
```csharp  
using System.Runtime.InteropServices;  
[DllImport("user32.dll")]  
    public static extern IntPtr MessageBox(int hWnd, String text,   
                                       String caption, uint type);  
```  
  
```cpp  
using namespace System::Runtime::InteropServices;  
[DllImport("user32.dll")]  
    extern "C" IntPtr MessageBox(int hWnd, String* pText,  
    String* pCaption unsigned int uType);  
```  
  
## <a name="adjusting-the-definition"></a><span data-ttu-id="f2bc0-116">Ajustement de la définition</span><span class="sxs-lookup"><span data-stu-id="f2bc0-116">Adjusting the Definition</span></span>  
 <span data-ttu-id="f2bc0-117">Que vous les définissiez explicitement ou non, les champs d'attribut définissent le comportement du code managé.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-117">Whether you set them explicitly or not, attribute fields are at work defining the behavior of managed code.</span></span> <span data-ttu-id="f2bc0-118">L'appel de code non managé agit selon les valeurs par défaut définies dans les différents champs qui existent sous la forme de métadonnées d'assembly.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-118">Platform invoke operates according to the default values set on various fields that exist as metadata in an assembly.</span></span> <span data-ttu-id="f2bc0-119">Vous pouvez modifier ce comportement par défaut en ajustant les valeurs d'un ou plusieurs champs.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-119">You can alter this default behavior by adjusting the values of one or more fields.</span></span> <span data-ttu-id="f2bc0-120">Dans de nombreux cas, vous utilisez <xref:System.Runtime.InteropServices.DllImportAttribute> pour définir une valeur.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-120">In many cases, you use the <xref:System.Runtime.InteropServices.DllImportAttribute> to set a value.</span></span>  
  
 <span data-ttu-id="f2bc0-121">Le tableau suivant répertorie l'ensemble complet des champs d'attribut qui se rapportent aux appels de code non managé.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-121">The following table lists the complete set of attribute fields that pertain to platform invoke.</span></span> <span data-ttu-id="f2bc0-122">Pour chaque champ, le tableau inclut la valeur par défaut et un lien vers des informations sur la façon d'utiliser ces champs pour définir des fonctions DLL non managées.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-122">For each field, the table includes the default value and a link to information on how to use these fields to define unmanaged DLL functions.</span></span>  
  
|<span data-ttu-id="f2bc0-123">Champ</span><span class="sxs-lookup"><span data-stu-id="f2bc0-123">Field</span></span>|<span data-ttu-id="f2bc0-124">Description</span><span class="sxs-lookup"><span data-stu-id="f2bc0-124">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|<span data-ttu-id="f2bc0-125">Active ou désactive le mappage ajusté.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-125">Enables or disables best-fit mapping.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|<span data-ttu-id="f2bc0-126">Spécifie la convention d’appel à utiliser lors du passage des arguments de méthode.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-126">Specifies the calling convention to use in passing method arguments.</span></span> <span data-ttu-id="f2bc0-127">La valeur par défaut est `WinAPI`, ce qui correspond à `__stdcall` pour les plateformes 32 bits Intel.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-127">The default is `WinAPI`, which corresponds to `__stdcall` for the 32-bit Intel-based platforms.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|<span data-ttu-id="f2bc0-128">Contrôle le troncage des noms et la façon dont les arguments de chaîne doivent être marshalés vers la fonction.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-128">Controls name mangling and the way that string arguments should be marshaled to the function.</span></span> <span data-ttu-id="f2bc0-129">La valeur par défaut est `CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-129">The default is `CharSet.Ansi`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|<span data-ttu-id="f2bc0-130">Spécifie le point d'entrée de DLL à appeler.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-130">Specifies the DLL entry point to be called.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|<span data-ttu-id="f2bc0-131">Détermine si un point d'entrée doit être modifié pour correspondre au jeu de caractères.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-131">Controls whether an entry point should be modified to correspond to the character set.</span></span> <span data-ttu-id="f2bc0-132">La valeur par défaut varie en fonction du langage de programmation.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-132">The default value varies by programming language.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|<span data-ttu-id="f2bc0-133">Contrôle si la signature de méthode managée doit être transformée en signature non managée qui retourne un HRESULT et possède un argument supplémentaire [out, retval] pour la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-133">Controls whether the managed method signature should be transformed into an unmanaged signature that returns an HRESULT and has an additional [out, retval] argument for the return value.</span></span><br /><br /> <span data-ttu-id="f2bc0-134">La valeur par défaut est `true` (la signature ne doit pas être transformée).</span><span class="sxs-lookup"><span data-stu-id="f2bc0-134">The default is `true` (the signature should not be transformed).</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|<span data-ttu-id="f2bc0-135">Permet à l'appelant d'utiliser la fonction d'API `Marshal.GetLastWin32Error` pour déterminer si une erreur s'est produite lors de l'exécution de la méthode.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-135">Enables the caller to use the `Marshal.GetLastWin32Error` API function to determine whether an error occurred while executing the method.</span></span> <span data-ttu-id="f2bc0-136">En Visual Basic, la valeur par défaut est `true` ; en C# et C++, la valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-136">In Visual Basic, the default is `true`; in C# and C++, the default is `false`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|<span data-ttu-id="f2bc0-137">Contrôle la levée d'une exception sur un caractère Unicode non mappable converti en un caractère ANSI "?".</span><span class="sxs-lookup"><span data-stu-id="f2bc0-137">Controls throwing of an exception on an unmappable Unicode character that is converted to an ANSI "?" character.</span></span>|  
  
 <span data-ttu-id="f2bc0-138">Pour obtenir des informations de référence détaillées, consultez <xref:System.Runtime.InteropServices.DllImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-138">For detailed reference information, see <xref:System.Runtime.InteropServices.DllImportAttribute>.</span></span>  
  
## <a name="platform-invoke-security-considerations"></a><span data-ttu-id="f2bc0-139">Considérations relatives à la sécurité des appels de code non managé</span><span class="sxs-lookup"><span data-stu-id="f2bc0-139">Platform invoke security considerations</span></span>  
 <span data-ttu-id="f2bc0-140">Les membres `Assert`, `Deny` et `PermitOnly` de l’énumération <xref:System.Security.Permissions.SecurityAction> sont appelés *modificateurs de parcours de pile*.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-140">The `Assert`, `Deny`, and `PermitOnly` members of the <xref:System.Security.Permissions.SecurityAction> enumeration are referred to as *stack walk modifiers*.</span></span> <span data-ttu-id="f2bc0-141">Ces membres sont ignorés s'ils sont utilisés comme des attributs déclaratifs sur des déclarations d'appel de code non managé et des instructions Interface Definition Language (IDL) COM.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-141">These members are ignored if they are used as declarative attributes on platform invoke declarations and COM Interface Definition Language (IDL) statements.</span></span>  
  
### <a name="platform-invoke-examples"></a><span data-ttu-id="f2bc0-142">Exemples d'appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="f2bc0-142">Platform Invoke Examples</span></span>  
 <span data-ttu-id="f2bc0-143">Les exemples d'appel de code non managé de cette section illustrent l'utilisation de l'attribut `RegistryPermission` avec les modificateurs de parcours de pile.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-143">The platform invoke samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="f2bc0-144">Dans l’exemple de code suivant, le <xref:System.Security.Permissions.SecurityAction> `Assert`, `Deny`, et `PermitOnly` modificateurs sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-144">In the following code example, the <xref:System.Security.Permissions.SecurityAction>`Assert`, `Deny`, and `PermitOnly` modifiers are ignored.</span></span>  
  
```  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionAssert();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="f2bc0-145">Toutefois, le modificateur `Demand` de l'exemple suivant est accepté.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-145">However, the `Demand` modifier in the following example is accepted.</span></span>  
  
```  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="f2bc0-146">Les modificateurs <xref:System.Security.Permissions.SecurityAction> fonctionnent correctement s'ils sont placés sur une classe qui contient (encapsule) l'appel de code non managé.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-146"><xref:System.Security.Permissions.SecurityAction> modifiers do work correctly if they are placed on a class that contains (wraps) the platform invoke call.</span></span>  
  
```cpp  
      [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
public ref class PInvokeWrapper  
{  
public:  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
};  
```  
  
```csharp  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
class PInvokeWrapper  
{  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
}  
```  
  
 <span data-ttu-id="f2bc0-147">Les modificateurs <xref:System.Security.Permissions.SecurityAction> fonctionnent également correctement dans un scénario d'imbrication dans lequel ils sont placés sur l'appelant de l'appel de code non managé :</span><span class="sxs-lookup"><span data-stu-id="f2bc0-147"><xref:System.Security.Permissions.SecurityAction> modifiers also work correctly in a nested scenario where they are placed on the caller of the platform invoke call:</span></span>  
  
```cpp  
      {  
public ref class PInvokeWrapper  
public:  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
  
    [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
};  
```  
  
```csharp  
class PInvokeScenario  
{  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionInternal();  
  
    [RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
}  
```  
  
#### <a name="com-interop-examples"></a><span data-ttu-id="f2bc0-148">Exemples COM Interop</span><span class="sxs-lookup"><span data-stu-id="f2bc0-148">COM Interop Examples</span></span>  
 <span data-ttu-id="f2bc0-149">Les exemples COM Interop de cette section illustrent l'utilisation de l'attribut `RegistryPermission` avec les modificateurs de parcours de pile.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-149">The COM interop samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="f2bc0-150">Les déclarations d'interface COM Interop ignorent les modificateurs `Assert`, `Deny` et `PermitOnly` de façon similaire aux exemples d'appels de code non managé de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-150">The following COM interop interface declarations ignore the `Assert`, `Deny`, and `PermitOnly` modifiers, similarly to the platform invoke examples in the previous section.</span></span>  
  
```  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDenyStubsItf  
{  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
 <span data-ttu-id="f2bc0-151">En outre, le modificateur `Demand` n'est pas accepté dans les scénarios de déclaration d'interface COM Interop, comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="f2bc0-151">Additionally, the `Demand` modifier is not accepted in COM interop interface declaration scenarios, as shown in the following example.</span></span>  
  
```  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDemandStubsItf  
{  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f2bc0-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2bc0-152">See Also</span></span>  
 [<span data-ttu-id="f2bc0-153">Consommation de fonctions DLL non managées</span><span class="sxs-lookup"><span data-stu-id="f2bc0-153">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [<span data-ttu-id="f2bc0-154">Spécification d'un point d'entrée</span><span class="sxs-lookup"><span data-stu-id="f2bc0-154">Specifying an Entry Point</span></span>](../../../docs/framework/interop/specifying-an-entry-point.md)  
 [<span data-ttu-id="f2bc0-155">Spécification d'un jeu de caractères</span><span class="sxs-lookup"><span data-stu-id="f2bc0-155">Specifying a Character Set</span></span>](../../../docs/framework/interop/specifying-a-character-set.md)  
 [<span data-ttu-id="f2bc0-156">Exemples d'appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="f2bc0-156">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="f2bc0-157">Considérations sur la sécurité d’appel de plateforme</span><span class="sxs-lookup"><span data-stu-id="f2bc0-157">Platform Invoke Security Considerations</span></span>](http://msdn.microsoft.com/library/bbcc67f7-50b5-4917-88ed-cb15470409fb)  
 [<span data-ttu-id="f2bc0-158">Identification des fonctions des DLL</span><span class="sxs-lookup"><span data-stu-id="f2bc0-158">Identifying Functions in DLLs</span></span>](../../../docs/framework/interop/identifying-functions-in-dlls.md)  
 [<span data-ttu-id="f2bc0-159">Création d’une classe pour contenir des fonctions DLL</span><span class="sxs-lookup"><span data-stu-id="f2bc0-159">Creating a Class to Hold DLL Functions</span></span>](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md)  
 [<span data-ttu-id="f2bc0-160">Appel à une fonction DLL</span><span class="sxs-lookup"><span data-stu-id="f2bc0-160">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
