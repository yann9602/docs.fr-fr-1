---
title: "Guide pratique pour créer une clé de Registre et définir sa valeur en Visual Basic"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- RegistryKey.CreateSubKey
- RegistryKey.SetValue
dev_langs:
- VB
helpviewer_keywords:
- registry keys, creating
- registry, adding values
- registry, adding keys
- registry keys, setting values
- examples [Visual Basic], registry
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 106a98a1b15c37eb2cac05e1a681bf7dfed3543d
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="ad377-102">Guide pratique pour créer une clé de Registre et définir sa valeur en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ad377-102">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>
<span data-ttu-id="ad377-103">Vous pouvez utiliser la méthode `CreateSubKey` de l’objet `My.Computer.Registry` pour créer une clé de Registre.</span><span class="sxs-lookup"><span data-stu-id="ad377-103">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="ad377-104">Procédure</span><span class="sxs-lookup"><span data-stu-id="ad377-104">Procedure</span></span>  
  
#### <a name="to-create-a-registry-key"></a><span data-ttu-id="ad377-105">Pour créer une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="ad377-105">To create a registry key</span></span>  
  
-   <span data-ttu-id="ad377-106">Utilisez la méthode `CreateSubKey`, en spécifiant le nom de la clé et sous quelle ruche la placer.</span><span class="sxs-lookup"><span data-stu-id="ad377-106">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="ad377-107">Le paramètre `Subkey` ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="ad377-107">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="ad377-108">Cet exemple crée la clé de Registre `MyTestKey` sous HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="ad377-108">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>  
  
     <span data-ttu-id="ad377-109">[!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ad377-109">[!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]</span></span>  
  
#### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="ad377-110">Pour créer une clé de Registre et définir sa valeur</span><span class="sxs-lookup"><span data-stu-id="ad377-110">To create a registry key and set a value in it</span></span>  
  
1.  <span data-ttu-id="ad377-111">Utilisez la méthode `CreateSubkey`, en spécifiant le nom de la clé et sous quelle ruche la placer.</span><span class="sxs-lookup"><span data-stu-id="ad377-111">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="ad377-112">Cet exemple crée la clé de Registre `MyTestKey` sous HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="ad377-112">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>  
  
     <span data-ttu-id="ad377-113">[!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ad377-113">[!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]</span></span>  
  
2.  <span data-ttu-id="ad377-114">Définissez la valeur avec la méthode `SetValue`.</span><span class="sxs-lookup"><span data-stu-id="ad377-114">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="ad377-115">Cet exemple définit « This is a test value »</span><span class="sxs-lookup"><span data-stu-id="ad377-115">This example sets the string value.</span></span> <span data-ttu-id="ad377-116">comme valeur de chaîne « MyTestKeyValue ».</span><span class="sxs-lookup"><span data-stu-id="ad377-116">"MyTestKeyValue" to "This is a test value".</span></span>  
  
     <span data-ttu-id="ad377-117">[!code-vb[VbResourceTasks#14](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="ad377-117">[!code-vb[VbResourceTasks#14](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad377-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="ad377-118">Example</span></span>  
 <span data-ttu-id="ad377-119">Cet exemple crée la clé de Registre `MyTestKey` sous HKEY_CURRENT_USER, puis affecte `This is a test value` comme valeur de chaîne `MyTestKeyValue`.</span><span class="sxs-lookup"><span data-stu-id="ad377-119">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>  
  
 <span data-ttu-id="ad377-120">[!code-vb[VbResourceTasks#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="ad377-120">[!code-vb[VbResourceTasks#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_3.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ad377-121">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="ad377-121">Robust Programming</span></span>  
 <span data-ttu-id="ad377-122">Examinez la structure du Registre pour rechercher un emplacement approprié pour votre clé.</span><span class="sxs-lookup"><span data-stu-id="ad377-122">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="ad377-123">Par exemple, vous souhaiterez peut-être ouvrir la clé HKEY_CURRENT_USER\Software de l’utilisateur actuel et créer une clé avec le nom de votre société.</span><span class="sxs-lookup"><span data-stu-id="ad377-123">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="ad377-124">Ensuite, ajoutez les valeurs de Registre à la clé de votre société.</span><span class="sxs-lookup"><span data-stu-id="ad377-124">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="ad377-125">Lors de la lecture du Registre à partir d’une application web, l’utilisateur actuel dépend de l’authentification et de l’emprunt d’identité implémenté dans l’application web.</span><span class="sxs-lookup"><span data-stu-id="ad377-125">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
 <span data-ttu-id="ad377-126">Il est plus sûr d’écrire des données dans le dossier utilisateur (<xref:Microsoft.Win32.Registry.CurrentUser>) que sur l’ordinateur local (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="ad377-126">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>  
  
 <span data-ttu-id="ad377-127">Quand vous créez une valeur de Registre, vous devez déterminer ce qu’il faut faire si cette valeur existe déjà.</span><span class="sxs-lookup"><span data-stu-id="ad377-127">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="ad377-128">Il est possible qu’un autre processus, éventuellement malveillant, ait déjà créé la valeur et y ait accès.</span><span class="sxs-lookup"><span data-stu-id="ad377-128">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="ad377-129">Quand vous placez des données dans la valeur de Registre, ces données sont accessibles à l’autre processus.</span><span class="sxs-lookup"><span data-stu-id="ad377-129">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="ad377-130">Pour l’éviter, utilisez la méthode <xref:Microsoft.Win32.RegistryKey.GetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="ad377-130">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="ad377-131">Elle retourne `Nothing` si la clé n’existe pas encore.</span><span class="sxs-lookup"><span data-stu-id="ad377-131">It returns `Nothing` if the key does not already exist.</span></span>  
  
 <span data-ttu-id="ad377-132">Il est dangereux de stocker des données confidentielles (telles que des mots de passe) dans le Registre sous forme de texte brut, même si la clé de Registre est protégée par des listes de contrôle d’accès.</span><span class="sxs-lookup"><span data-stu-id="ad377-132">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>  
  
 <span data-ttu-id="ad377-133">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="ad377-133">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="ad377-134">Le nom de la clé est `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="ad377-134">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="ad377-135">L’utilisateur ne dispose pas des autorisations nécessaires pour créer des clés de Registre (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="ad377-135">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="ad377-136">Le nom de la clé dépasse la limite de 255 caractères (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="ad377-136">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="ad377-137">La clé est fermée (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="ad377-137">The key is closed (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="ad377-138">La clé de Registre est en lecture seule (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="ad377-138">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ad377-139">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ad377-139">.NET Framework Security</span></span>  
 <span data-ttu-id="ad377-140">Pour exécuter ce processus, votre assembly nécessite un niveau de privilège accordé par la classe <xref:System.Security.Permissions.RegistryPermission>.</span><span class="sxs-lookup"><span data-stu-id="ad377-140">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="ad377-141">Si vous l’exécutez dans un contexte de confiance partielle, le processus peut lever une exception en raison de privilèges insuffisants.</span><span class="sxs-lookup"><span data-stu-id="ad377-141">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="ad377-142">De même, l’utilisateur doit disposer de listes de contrôle d’accès (ACL) valides pour créer ou écrire des paramètres.</span><span class="sxs-lookup"><span data-stu-id="ad377-142">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="ad377-143">Par exemple, une application locale qui dispose de l’autorisation de sécurité d’accès du code peut ne pas disposer des autorisations de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="ad377-143">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="ad377-144">Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](https://msdn.microsoft.com/library/33tceax8).</span><span class="sxs-lookup"><span data-stu-id="ad377-144">For more information, see [Code Access Security Basics](https://msdn.microsoft.com/library/33tceax8).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad377-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad377-145">See Also</span></span>  
 <span data-ttu-id="ad377-146"><xref:Microsoft.VisualBasic.MyServices.RegistryProxy></span><span class="sxs-lookup"><span data-stu-id="ad377-146"><xref:Microsoft.VisualBasic.MyServices.RegistryProxy></span></span>   
 <span data-ttu-id="ad377-147"><xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A></span><span class="sxs-lookup"><span data-stu-id="ad377-147"><xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A></span></span>   
 <span data-ttu-id="ad377-148"><xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A></span><span class="sxs-lookup"><span data-stu-id="ad377-148"><xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A></span></span>   
 <span data-ttu-id="ad377-149">[Lecture et écriture dans le Registre](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md) </span><span class="sxs-lookup"><span data-stu-id="ad377-149">[Reading from and Writing to the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md) </span></span>  
 [<span data-ttu-id="ad377-150">Notions fondamentales de la sécurité d’accès du code</span><span class="sxs-lookup"><span data-stu-id="ad377-150">Code Access Security Basics</span></span>](https://msdn.microsoft.com/library/33tceax8)

