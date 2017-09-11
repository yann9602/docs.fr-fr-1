---
title: "Guide pratique pour créer une clé dans le Registre (Visual C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 96d34df3314494fc96ad8b55d7462b67dcc7bd72
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-key-in-the-registry-visual-c"></a><span data-ttu-id="9b5bf-102">Guide pratique pour créer une clé dans le Registre (Visual C#)</span><span class="sxs-lookup"><span data-stu-id="9b5bf-102">How to: Create a Key In the Registry (Visual C#)</span></span>
<span data-ttu-id="9b5bf-103">Cet exemple ajoute la paire de valeurs « Name » et « Isabella » dans le Registre de l’utilisateur actuel, sous la clé « Names ».</span><span class="sxs-lookup"><span data-stu-id="9b5bf-103">This example adds the value pair, "Name" and "Isabella", to the current user's registry, under the key "Names".</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b5bf-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="9b5bf-104">Example</span></span>  
  
```  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9b5bf-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="9b5bf-105">Compiling the Code</span></span>  
  
-   <span data-ttu-id="9b5bf-106">Copiez le code et collez-le dans la méthode `Main` d’une application console.</span><span class="sxs-lookup"><span data-stu-id="9b5bf-106">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
-   <span data-ttu-id="9b5bf-107">Remplacez le paramètre `Names` par le nom d’une clé qui existe directement sous le nœud HKEY_CURRENT_USER du Registre.</span><span class="sxs-lookup"><span data-stu-id="9b5bf-107">Replace the `Names` parameter with the name of a key that exists directly under the HKEY_CURRENT_USER node of the registry.</span></span>  
  
-   <span data-ttu-id="9b5bf-108">Remplacez le paramètre `Name` par le nom d’une valeur qui existe directement sous le nœud Names.</span><span class="sxs-lookup"><span data-stu-id="9b5bf-108">Replace the `Name` parameter with the name of a value that exists directly under the Names node.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9b5bf-109">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="9b5bf-109">Robust Programming</span></span>  
 <span data-ttu-id="9b5bf-110">Examinez la structure du Registre pour rechercher un emplacement approprié pour votre clé.</span><span class="sxs-lookup"><span data-stu-id="9b5bf-110">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="9b5bf-111">Par exemple, vous souhaiterez peut-être ouvrir la clé Software de l’utilisateur actuel et créer une clé avec le nom de votre société.</span><span class="sxs-lookup"><span data-stu-id="9b5bf-111">For example, you might want to open the Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="9b5bf-112">Ensuite, ajoutez les valeurs de Registre à la clé de votre société.</span><span class="sxs-lookup"><span data-stu-id="9b5bf-112">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="9b5bf-113">Les conditions ci-dessous peuvent générer une exception :</span><span class="sxs-lookup"><span data-stu-id="9b5bf-113">The following conditions might cause an exception:</span></span>  
  
-   <span data-ttu-id="9b5bf-114">Le nom de la clé est null.</span><span class="sxs-lookup"><span data-stu-id="9b5bf-114">The name of the key is null.</span></span>  
  
-   <span data-ttu-id="9b5bf-115">L’utilisateur ne dispose pas des autorisations nécessaires pour créer des clés de Registre.</span><span class="sxs-lookup"><span data-stu-id="9b5bf-115">The user does not have permissions to create registry keys.</span></span>  
  
-   <span data-ttu-id="9b5bf-116">Le nom de la clé dépasse la limite de 255 caractères.</span><span class="sxs-lookup"><span data-stu-id="9b5bf-116">The key name exceeds the 255-character limit.</span></span>  
  
-   <span data-ttu-id="9b5bf-117">La clé est fermée.</span><span class="sxs-lookup"><span data-stu-id="9b5bf-117">The key is closed.</span></span>  
  
-   <span data-ttu-id="9b5bf-118">La clé de Registre est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="9b5bf-118">The registry key is read-only.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9b5bf-119">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9b5bf-119">.NET Framework Security</span></span>  
 <span data-ttu-id="9b5bf-120">Il est plus sûr d’écrire des données dans le dossier utilisateur (`Microsoft.Win32.Registry.CurrentUser`) que sur l’ordinateur local (`Microsoft.Win32.Registry.LocalMachine`).</span><span class="sxs-lookup"><span data-stu-id="9b5bf-120">It is more secure to write data to the user folder — `Microsoft.Win32.Registry.CurrentUser` — rather than to the local computer — `Microsoft.Win32.Registry.LocalMachine`.</span></span>  
  
 <span data-ttu-id="9b5bf-121">Quand vous créez une valeur de Registre, vous devez déterminer ce qu’il faut faire si cette valeur existe déjà.</span><span class="sxs-lookup"><span data-stu-id="9b5bf-121">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="9b5bf-122">Il est possible qu’un autre processus, éventuellement malveillant, ait déjà créé la valeur et y ait accès.</span><span class="sxs-lookup"><span data-stu-id="9b5bf-122">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="9b5bf-123">Quand vous placez des données dans la valeur de Registre, ces données sont accessibles à l’autre processus.</span><span class="sxs-lookup"><span data-stu-id="9b5bf-123">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="9b5bf-124">Pour éviter ce problème, utilisez la méthode `Overload:Microsoft.Win32.RegistryKey.GetValue`</span><span class="sxs-lookup"><span data-stu-id="9b5bf-124">To prevent this, use the.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span></span> <span data-ttu-id="9b5bf-125">.</span><span class="sxs-lookup"><span data-stu-id="9b5bf-125">method.</span></span> <span data-ttu-id="9b5bf-126">Elle retourne null si la clé n’existe pas encore.</span><span class="sxs-lookup"><span data-stu-id="9b5bf-126">It returns null if the key does not already exist.</span></span>  
  
 <span data-ttu-id="9b5bf-127">Il est dangereux de stocker des données confidentielles, telles que des mots de passe, dans le Registre sous forme de texte brut, même si la clé de Registre est protégée par des listes de contrôle d’accès.</span><span class="sxs-lookup"><span data-stu-id="9b5bf-127">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by access control lists (ACL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b5bf-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b5bf-128">See Also</span></span>  
 <span data-ttu-id="9b5bf-129"><xref:System.IO?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9b5bf-129"><xref:System.IO?displayProperty=fullName></span></span>   
 <span data-ttu-id="9b5bf-130">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9b5bf-130">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9b5bf-131">[Système de fichiers et Registre (Guide de programmation C#)](../../../csharp/programming-guide/file-system/index.md) </span><span class="sxs-lookup"><span data-stu-id="9b5bf-131">[File System and the Registry (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md) </span></span>  
 [<span data-ttu-id="9b5bf-132">Read, write and delete from the registry with C# (Lire, écrire et supprimer du Registre avec C#)</span><span class="sxs-lookup"><span data-stu-id="9b5bf-132">Read, write and delete from the registry with C#</span></span>](http://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)

