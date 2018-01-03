---
title: "Marshaling par défaut pour les chaînes"
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
- strings, interop marshaling
- interop marshaling, strings
ms.assetid: 9baea3ce-27b3-4b4f-af98-9ad0f9467e6f
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f8de04f9674e67bf1498fb8f25f2b3c61fec438
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="default-marshaling-for-strings"></a><span data-ttu-id="e616f-102">Marshaling par défaut pour les chaînes</span><span class="sxs-lookup"><span data-stu-id="e616f-102">Default Marshaling for Strings</span></span>
<span data-ttu-id="e616f-103">Les classes <xref:System.String?displayProperty=nameWithType> et <xref:System.Text.StringBuilder?displayProperty=nameWithType> ont un comportement de marshaling semblable.</span><span class="sxs-lookup"><span data-stu-id="e616f-103">Both the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes have similar marshaling behavior.</span></span>  
  
 <span data-ttu-id="e616f-104">Les chaînes sont marshalées en tant que type `BSTR` de style COM ou comme une chaîne se terminant par un caractère Null (un tableau de caractères se terminant par un caractère Null).</span><span class="sxs-lookup"><span data-stu-id="e616f-104">Strings are marshaled as a COM-style `BSTR` type or as a null-terminated string (a character array that ends with a null character).</span></span> <span data-ttu-id="e616f-105">Les caractères de la chaîne peuvent être marshalés en tant que caractères Unicode (valeur par défaut sur les systèmes Windows) ou ANSI.</span><span class="sxs-lookup"><span data-stu-id="e616f-105">The characters within the string can be marshaled as Unicode (the default on Windows systems) or ANSI.</span></span>  
  
 <span data-ttu-id="e616f-106">Cette rubrique fournit les informations suivantes sur le marshaling des types de chaînes :</span><span class="sxs-lookup"><span data-stu-id="e616f-106">This topic provides the following information on marshaling string types:</span></span>  
  
-   [<span data-ttu-id="e616f-107">Chaînes utilisées dans les interfaces</span><span class="sxs-lookup"><span data-stu-id="e616f-107">Strings Used in Interfaces</span></span>](#cpcondefaultmarshalingforstringsanchor1)  
  
-   [<span data-ttu-id="e616f-108">Chaînes utilisées dans les appels de code non managé</span><span class="sxs-lookup"><span data-stu-id="e616f-108">Strings Used in Platform Invoke</span></span>](#cpcondefaultmarshalingforstringsanchor5)  
  
-   [<span data-ttu-id="e616f-109">Chaînes utilisées dans les structures</span><span class="sxs-lookup"><span data-stu-id="e616f-109">Strings Used in Structures</span></span>](#cpcondefaultmarshalingforstringsanchor2)  
  
-   [<span data-ttu-id="e616f-110">Mémoires tampons de chaînes de longueur fixe</span><span class="sxs-lookup"><span data-stu-id="e616f-110">Fixed-Length String Buffers</span></span>](#cpcondefaultmarshalingforstringsanchor3)  
  
<a name="cpcondefaultmarshalingforstringsanchor1"></a>   
## <a name="strings-used-in-interfaces"></a><span data-ttu-id="e616f-111">Chaînes utilisées dans les interfaces</span><span class="sxs-lookup"><span data-stu-id="e616f-111">Strings Used in Interfaces</span></span>  
 <span data-ttu-id="e616f-112">Le tableau suivant montre les options de marshaling pour le type de données String quand il est marshalé comme un argument de méthode du code non managé.</span><span class="sxs-lookup"><span data-stu-id="e616f-112">The following table shows the marshaling options for the string data type when marshaled as a method argument to unmanaged code.</span></span> <span data-ttu-id="e616f-113">L'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> fournit plusieurs valeurs d'énumération <xref:System.Runtime.InteropServices.UnmanagedType> pour marshaler des chaînes d'interfaces COM.</span><span class="sxs-lookup"><span data-stu-id="e616f-113">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to COM interfaces.</span></span>  
  
|<span data-ttu-id="e616f-114">Type d'énumération</span><span class="sxs-lookup"><span data-stu-id="e616f-114">Enumeration type</span></span>|<span data-ttu-id="e616f-115">Description du format non managé</span><span class="sxs-lookup"><span data-stu-id="e616f-115">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="e616f-116">`UnmanagedType.BStr` (par défaut)</span><span class="sxs-lookup"><span data-stu-id="e616f-116">`UnmanagedType.BStr` (default)</span></span>|<span data-ttu-id="e616f-117">`BSTR` de style COM avec une longueur prédéfinie et des caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="e616f-117">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="e616f-118">Pointeur vers un tableau de caractères ANSI terminé par un caractère Null.</span><span class="sxs-lookup"><span data-stu-id="e616f-118">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="e616f-119">Pointeur vers un tableau de caractères Unicode terminé par un caractère null.</span><span class="sxs-lookup"><span data-stu-id="e616f-119">A pointer to a null-terminated array of Unicode characters.</span></span>|  
  
 <span data-ttu-id="e616f-120">Ce tableau s'applique aux chaînes.</span><span class="sxs-lookup"><span data-stu-id="e616f-120">This table applies to strings.</span></span> <span data-ttu-id="e616f-121">Toutefois, pour <xref:System.Text.StringBuilder>, les seules options autorisées sont `UnmanagedType.LPStr` et `UnmanagedType.LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="e616f-121">However, for <xref:System.Text.StringBuilder>, the only options allowed are `UnmanagedType.LPStr` and `UnmanagedType.LPWStr`.</span></span>  
  
 <span data-ttu-id="e616f-122">L'exemple suivant montre des chaînes déclarées dans l'interface `IStringWorker`.</span><span class="sxs-lookup"><span data-stu-id="e616f-122">The following example shows strings declared in the `IStringWorker` interface.</span></span>  
  
```cpp  
public interface IStringWorker {  
void PassString1(String s);  
void PassString2([MarshalAs(UnmanagedType.BStr)]String s);  
void PassString3([MarshalAs(UnmanagedType.LPStr)]String s);  
void PassString4([MarshalAs(UnmanagedType.LPWStr)]String s);  
void PassStringRef1(ref String s);  
void PassStringRef2([MarshalAs(UnmanagedType.BStr)]ref String s);  
void PassStringRef3([MarshalAs(UnmanagedType.LPStr)]ref String s);  
void PassStringRef4([MarshalAs(UnmanagedType.LPWStr)]ref String s);  
);  
```  
  
 <span data-ttu-id="e616f-123">L'exemple suivant montre l'interface correspondante décrite dans une bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="e616f-123">The following example shows the corresponding interface described in a type library.</span></span>  
  
```  
[…]  
interface IStringWorker : IDispatch {  
HRESULT PassString1([in] BSTR s);  
HRESULT PassString2([in] BSTR s);  
HRESULT PassString3([in] LPStr s);  
HRESULT PassString4([in] LPWStr s);  
HRESULT PassStringRef1([in, out] BSTR *s);  
HRESULT PassStringRef2([in, out] BSTR *s);  
HRESULT PassStringRef3([in, out] LPStr *s);  
HRESULT PassStringRef4([in, out] LPWStr *s);  
);  
```  
  
<a name="cpcondefaultmarshalingforstringsanchor5"></a>   
## <a name="strings-used-in-platform-invoke"></a><span data-ttu-id="e616f-124">Chaînes utilisées dans les appels de code non managé</span><span class="sxs-lookup"><span data-stu-id="e616f-124">Strings Used in Platform Invoke</span></span>  
 <span data-ttu-id="e616f-125">L'appel de code non managé copie des arguments de chaîne, en convertissant du format .NET Framework (Unicode) au format non managé de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="e616f-125">Platform invoke copies string arguments, converting from the .NET Framework format (Unicode) to the platform unmanaged format.</span></span> <span data-ttu-id="e616f-126">Les chaînes sont immuables et ne sont pas copiées depuis la mémoire non managée vers la mémoire managée quand l'appel est retourné.</span><span class="sxs-lookup"><span data-stu-id="e616f-126">Strings are immutable and are not copied back from unmanaged memory to managed memory when the call returns.</span></span>  
  
 <span data-ttu-id="e616f-127">Le tableau suivant répertorie les options de marshaling pour les chaînes quand celles-ci sont marshalées comme un argument de méthode d'un appel de code non managé.</span><span class="sxs-lookup"><span data-stu-id="e616f-127">The following table lists the marshaling options for strings when marshaled as a method argument of a platform invoke call.</span></span> <span data-ttu-id="e616f-128">L'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> fournit plusieurs valeurs d'énumération <xref:System.Runtime.InteropServices.UnmanagedType> pour marshaler les chaînes.</span><span class="sxs-lookup"><span data-stu-id="e616f-128">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings.</span></span>  
  
|<span data-ttu-id="e616f-129">Type d'énumération</span><span class="sxs-lookup"><span data-stu-id="e616f-129">Enumeration type</span></span>|<span data-ttu-id="e616f-130">Description du format non managé</span><span class="sxs-lookup"><span data-stu-id="e616f-130">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|`UnmanagedType.AnsiBStr`|<span data-ttu-id="e616f-131">`BSTR` de style COM avec une longueur prédéfinie et des caractères ANSI.</span><span class="sxs-lookup"><span data-stu-id="e616f-131">A COM-style `BSTR` with a prefixed length and ANSI characters.</span></span>|  
|`UnmanagedType.BStr`|<span data-ttu-id="e616f-132">`BSTR` de style COM avec une longueur prédéfinie et des caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="e616f-132">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="e616f-133">Pointeur vers un tableau de caractères ANSI terminé par un caractère Null.</span><span class="sxs-lookup"><span data-stu-id="e616f-133">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPTStr`|<span data-ttu-id="e616f-134">Pointeur vers un tableau de caractères dépendant de la plateforme se terminant par un caractère Null.</span><span class="sxs-lookup"><span data-stu-id="e616f-134">A pointer to a null-terminated array of platform-dependent characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="e616f-135">Pointeur vers un tableau de caractères Unicode terminé par un caractère null.</span><span class="sxs-lookup"><span data-stu-id="e616f-135">A pointer to a null-terminated array of Unicode characters.</span></span>|  
|`UnmanagedType.TBStr`|<span data-ttu-id="e616f-136">`BSTR` de style COM de longueur fixe avec des caractères dépendant de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="e616f-136">A COM-style `BSTR` with a prefixed length and platform-dependent characters.</span></span>|  
|`VBByRefStr`|<span data-ttu-id="e616f-137">Valeur qui permet à Visual Basic .NET de changer une chaîne dans du code non managé et de répercuter les résultats dans du code managé.</span><span class="sxs-lookup"><span data-stu-id="e616f-137">A value that enables Visual Basic .NET to change a string in unmanaged code, and have the results reflected in managed code.</span></span> <span data-ttu-id="e616f-138">Cette valeur est prise en charge uniquement pour l'appel de code non managé.</span><span class="sxs-lookup"><span data-stu-id="e616f-138">This value is supported only for platform invoke.</span></span> <span data-ttu-id="e616f-139">Il s’agit de la valeur par défaut dans Visual Basic pour les chaînes `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="e616f-139">This is default value in Visual Basic for `ByVal` strings.</span></span>|  
  
 <span data-ttu-id="e616f-140">Ce tableau s'applique aux chaînes.</span><span class="sxs-lookup"><span data-stu-id="e616f-140">This table applies to strings.</span></span> <span data-ttu-id="e616f-141">Toutefois, pour <xref:System.Text.StringBuilder>, les seules options autorisées sont `LPStr`, `LPTStr` et `LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="e616f-141">However, for <xref:System.Text.StringBuilder>, the only options allowed are `LPStr`, `LPTStr`, and `LPWStr`.</span></span>  
  
 <span data-ttu-id="e616f-142">La définition de type suivante montre une utilisation correcte de `MarshalAsAttribute` pour les appels de code non managé.</span><span class="sxs-lookup"><span data-stu-id="e616f-142">The following type definition shows the correct use of `MarshalAsAttribute` for platform invoke calls.</span></span>  
  
```vb  
Class StringLibAPI      
Public Declare Auto Sub PassLPStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPStr)> s As String)      
Public Declare Auto Sub PassLPWStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPWStr)> s As String)      
Public Declare Auto Sub PassLPTStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPTStr)> s As String)      
Public Declare Auto Sub PassBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.BStr)> s As String)      
Public Declare Auto Sub PassAnsiBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.AnsiBStr)> s As String)      
Public Declare Auto Sub PassTBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.TBStr)> s As String)  
End Class  
```  
  
```csharp  
class StringLibAPI {  
[DllImport("StringLib.Dll")]  
public static extern void PassLPStr([MarshalAs(UnmanagedType.LPStr)]  
String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassLPWStr([MarshalAs(UnmanagedType.LPWStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassLPTStr([MarshalAs(UnmanagedType.LPTStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void PassBStr([MarshalAs(UnmanagedType.BStr)]  
String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassAnsiBStr([MarshalAs(UnmanagedType.AnsiBStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void PassTBStr([MarshalAs(UnmanagedType.TBStr)]  
String s);  
}  
```  
  
<a name="cpcondefaultmarshalingforstringsanchor2"></a>   
## <a name="strings-used-in-structures"></a><span data-ttu-id="e616f-143">Chaînes utilisées dans les structures</span><span class="sxs-lookup"><span data-stu-id="e616f-143">Strings Used in Structures</span></span>  
 <span data-ttu-id="e616f-144">Les chaînes sont des membres valides de structures. Toutefois, les mémoires tampons <xref:System.Text.StringBuilder> ne sont pas valides dans les structures.</span><span class="sxs-lookup"><span data-stu-id="e616f-144">Strings are valid members of structures; however, <xref:System.Text.StringBuilder> buffers are invalid in structures.</span></span> <span data-ttu-id="e616f-145">Le tableau suivant montre les options de marshaling pour le type de données String quand le type est marshalé en tant que champ.</span><span class="sxs-lookup"><span data-stu-id="e616f-145">The following table shows the marshaling options for the string data type when the type is marshaled as a field.</span></span> <span data-ttu-id="e616f-146">L'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> fournit plusieurs valeurs d'énumération <xref:System.Runtime.InteropServices.UnmanagedType> pour marshaler les chaînes en tant que champ.</span><span class="sxs-lookup"><span data-stu-id="e616f-146">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to a field.</span></span>  
  
|<span data-ttu-id="e616f-147">Type d'énumération</span><span class="sxs-lookup"><span data-stu-id="e616f-147">Enumeration type</span></span>|<span data-ttu-id="e616f-148">Description du format non managé</span><span class="sxs-lookup"><span data-stu-id="e616f-148">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr`|<span data-ttu-id="e616f-149">`BSTR` de style COM avec une longueur prédéfinie et des caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="e616f-149">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="e616f-150">Pointeur vers un tableau de caractères ANSI terminé par un caractère Null.</span><span class="sxs-lookup"><span data-stu-id="e616f-150">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPTStr`|<span data-ttu-id="e616f-151">Pointeur vers un tableau de caractères dépendant de la plateforme se terminant par un caractère Null.</span><span class="sxs-lookup"><span data-stu-id="e616f-151">A pointer to a null-terminated array of platform-dependent characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="e616f-152">Pointeur vers un tableau de caractères Unicode terminé par un caractère null.</span><span class="sxs-lookup"><span data-stu-id="e616f-152">A pointer to a null-terminated array of Unicode characters.</span></span>|  
|`UnmanagedType.ByValTStr`|<span data-ttu-id="e616f-153">Tableau de caractères de longueur fixe. Le type du tableau est déterminé par le jeu de caractères de la structure contenante.</span><span class="sxs-lookup"><span data-stu-id="e616f-153">A fixed-length array of characters; the array's type is determined by the character set of the containing structure.</span></span>|  
  
 <span data-ttu-id="e616f-154">Le type `ByValTStr` est utilisé pour les tableaux de caractères inline de longueur fixe qui sont situés dans une structure.</span><span class="sxs-lookup"><span data-stu-id="e616f-154">The `ByValTStr` type is used for inline, fixed-length character arrays that appear within a structure.</span></span> <span data-ttu-id="e616f-155">D'autres types s'appliquent aux références de chaîne contenues au sein de structures qui contiennent des pointeurs vers des chaînes.</span><span class="sxs-lookup"><span data-stu-id="e616f-155">Other types apply to string references contained within structures that contain pointers to strings.</span></span>  
  
 <span data-ttu-id="e616f-156">L'argument `CharSet` de l'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> qui est appliqué à la structure contenante détermine le format de caractères des chaînes des structures.</span><span class="sxs-lookup"><span data-stu-id="e616f-156">The `CharSet` argument of the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute that is applied to the containing structure determines the character format of strings in structures.</span></span> <span data-ttu-id="e616f-157">Les exemples de structures suivants contiennent des références de chaîne et des chaînes inline, ainsi que des caractères ANSI, Unicode et dépendant de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="e616f-157">The following example structures contain string references and inline strings, as well as ANSI, Unicode, and platform-dependent characters.</span></span>  
  
### <a name="type-library-representation"></a><span data-ttu-id="e616f-158">Représentation d'une bibliothèque de types</span><span class="sxs-lookup"><span data-stu-id="e616f-158">Type Library Representation</span></span>  
  
```  
struct StringInfoA {  
   char *    f1;  
   char      f2[256];  
};  
struct StringInfoW {  
   WCHAR *   f1;  
   WCHAR     f2[256];  
   BSTR      f3;  
};  
struct StringInfoT {  
   TCHAR *   f1;  
   TCHAR     f2[256];  
};  
```  
  
 <span data-ttu-id="e616f-159">L'exemple de code suivant montre comment utiliser l'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> pour définir une même structure dans des formats différents.</span><span class="sxs-lookup"><span data-stu-id="e616f-159">The following code example shows how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to define the same structure in different formats.</span></span>  
  
```vb  
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Ansi)> _  
Structure StringInfoA  
<MarshalAs(UnmanagedType.LPStr)> Public f1 As String  
<MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _  
Public f2 As String  
End Structure  
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Unicode)> _  
Structure StringInfoW  
<MarshalAs(UnmanagedType.LPWStr)> Public f1 As String  
<MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _  
Public f2 As String  
<MarshalAs(UnmanagedType.BStr)> Public f3 As String  
End Structure  
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Auto)> _  
Structure StringInfoT  
<MarshalAs(UnmanagedType.LPTStr)> Public f1 As String  
<MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _  
Public f2 As String  
End Structure  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Ansi)]  
struct StringInfoA {  
   [MarshalAs(UnmanagedType.LPStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
}  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Unicode)]  
struct StringInfoW {  
   [MarshalAs(UnmanagedType.LPWStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
   [MarshalAs(UnmanagedType.BStr)] public String f3;  
}  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Auto)]  
struct StringInfoT {  
   [MarshalAs(UnmanagedType.LPTStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
}  
```  
  
<a name="cpcondefaultmarshalingforstringsanchor3"></a>   
## <a name="fixed-length-string-buffers"></a><span data-ttu-id="e616f-160">Mémoires tampons de chaînes de longueur fixe</span><span class="sxs-lookup"><span data-stu-id="e616f-160">Fixed-Length String Buffers</span></span>  
 <span data-ttu-id="e616f-161">Dans certains cas, une mémoire tampon de caractères de longueur fixe doit être passée à du code non managé pour pouvoir être manipulée.</span><span class="sxs-lookup"><span data-stu-id="e616f-161">In some circumstances, a fixed-length character buffer must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="e616f-162">Le fait de passer une chaîne ne fonctionne pas dans ce cas, car l'appelé ne peut pas modifier le contenu de la mémoire tampon passée.</span><span class="sxs-lookup"><span data-stu-id="e616f-162">Simply passing a string does not work in this case because the callee cannot modify the contents of the passed buffer.</span></span> <span data-ttu-id="e616f-163">Même si la chaîne est passée par référence, il est impossible d'initialiser la mémoire tampon à une taille donnée.</span><span class="sxs-lookup"><span data-stu-id="e616f-163">Even if the string is passed by reference, there is no way to initialize the buffer to a given size.</span></span>  
  
 <span data-ttu-id="e616f-164">La solution consiste à passer une mémoire tampon <xref:System.Text.StringBuilder> comme un argument plutôt que comme une chaîne.</span><span class="sxs-lookup"><span data-stu-id="e616f-164">The solution is to pass a <xref:System.Text.StringBuilder> buffer as the argument instead of a string.</span></span> <span data-ttu-id="e616f-165">Un `StringBuilder` peut être déréférencé et modifié par l'appelé à condition qu'il ne dépasse pas la capacité de `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="e616f-165">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="e616f-166">Il peut également être initialisé à une longueur fixe.</span><span class="sxs-lookup"><span data-stu-id="e616f-166">It can also be initialized to a fixed length.</span></span> <span data-ttu-id="e616f-167">Par exemple, si vous initialisez une mémoire tampon `StringBuilder` avec une capacité de `N`, le marshaleur fournira une mémoire tampon de (`N`+ 1) caractères.</span><span class="sxs-lookup"><span data-stu-id="e616f-167">For example, if you initialize a `StringBuilder` buffer to a capacity of `N`, the marshaler provides a buffer of size (`N`+1) characters.</span></span> <span data-ttu-id="e616f-168">Le +1 tient compte du fait que la chaîne non managée possède un terminateur Null, contrairement à `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="e616f-168">The +1 accounts for the fact that the unmanaged string has a null terminator while `StringBuilder` does not.</span></span>  
  
 <span data-ttu-id="e616f-169">Par exemple, la fonction `GetWindowText` de l'API Win32 de Microsoft (définie dans Windows.h) est une mémoire tampon de caractères de longueur fixe qui doit être passée dans du code non managé pour être manipulée.</span><span class="sxs-lookup"><span data-stu-id="e616f-169">For example, the Microsoft Win32 API `GetWindowText` function (defined in Windows.h) is a fixed-length character buffer that must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="e616f-170">`LpString` pointe vers une mémoire tampon allouée par l'appelant de taille `nMaxCount`.</span><span class="sxs-lookup"><span data-stu-id="e616f-170">`LpString` points to a caller-allocated buffer of size `nMaxCount`.</span></span> <span data-ttu-id="e616f-171">L'appelant est censé allouer la mémoire tampon et définir l'argument `nMaxCount` sur la taille de la mémoire tampon allouée.</span><span class="sxs-lookup"><span data-stu-id="e616f-171">The caller is expected to allocate the buffer and set the `nMaxCount` argument to the size of the allocated buffer.</span></span> <span data-ttu-id="e616f-172">Le code suivant illustre la déclaration de fonction `GetWindowText` définie dans Windows.h.</span><span class="sxs-lookup"><span data-stu-id="e616f-172">The following code shows the `GetWindowText` function declaration as defined in Windows.h.</span></span>  
  
```  
int GetWindowText(  
HWND hWnd,        // Handle to window or control.  
LPTStr lpString,  // Text buffer.  
int nMaxCount     // Maximum number of characters to copy.  
);  
```  
  
 <span data-ttu-id="e616f-173">Un `StringBuilder` peut être déréférencé et modifié par l'appelé à condition qu'il ne dépasse pas la capacité de `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="e616f-173">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="e616f-174">L'exemple de code suivant montre comment `StringBuilder` peut être initialisé à une longueur fixe.</span><span class="sxs-lookup"><span data-stu-id="e616f-174">The following code example demonstrates how `StringBuilder` can be initialized to a fixed length.</span></span>  
  
```vb  
Public Class Win32API  
Public Declare Auto Sub GetWindowText Lib "User32.Dll" _  
(h As Integer, s As StringBuilder, nMaxCount As Integer)  
End Class  
Public Class Window  
   Friend h As Integer ' Friend handle to Window.  
   Public Function GetText() As String  
      Dim sb As New StringBuilder(256)  
      Win32API.GetWindowText(h, sb, sb.Capacity + 1)  
   Return sb.ToString()  
   End Function  
End Class  
```  
  
```csharp  
public class Win32API {  
[DllImport("User32.Dll")]  
public static extern void GetWindowText(int h, StringBuilder s,   
int nMaxCount);  
}  
public class Window {  
   internal int h;        // Internal handle to Window.  
   public String GetText() {  
      StringBuilder sb = new StringBuilder(256);  
      Win32API.GetWindowText(h, sb, sb.Capacity + 1);  
   return sb.ToString();  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e616f-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e616f-175">See Also</span></span>  
 [<span data-ttu-id="e616f-176">Comportement de marshaling par défaut</span><span class="sxs-lookup"><span data-stu-id="e616f-176">Default Marshaling Behavior</span></span>](../../../docs/framework/interop/default-marshaling-behavior.md)  
 [<span data-ttu-id="e616f-177">Types blittable et non blittable</span><span class="sxs-lookup"><span data-stu-id="e616f-177">Blittable and Non-Blittable Types</span></span>](../../../docs/framework/interop/blittable-and-non-blittable-types.md)  
 [<span data-ttu-id="e616f-178">Attributs directionnels</span><span class="sxs-lookup"><span data-stu-id="e616f-178">Directional Attributes</span></span>](http://msdn.microsoft.com/en-us/241ac5b5-928e-4969-8f58-1dbc048f9ea2)  
 [<span data-ttu-id="e616f-179">Copie et épinglage</span><span class="sxs-lookup"><span data-stu-id="e616f-179">Copying and Pinning</span></span>](../../../docs/framework/interop/copying-and-pinning.md)
