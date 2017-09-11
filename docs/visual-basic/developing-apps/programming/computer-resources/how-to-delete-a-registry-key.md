---
title: "Guide pratique pour supprimer une clé de Registre en Visual Basic"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.DeleteSetting
dev_langs:
- VB
helpviewer_keywords:
- GetSetting function
- registry, deleting values
- GetAllSettings function
- registry keys, deleting
- registry, deleting keys
- examples [Visual Basic], registry
ms.assetid: ab9aca0e-42b0-4ff7-8ff9-845a4bfdf9f2
caps.latest.revision: 28
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
ms.openlocfilehash: 0fc37aff9f6a0ae3a7953377ebf95179d01bb693
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a><span data-ttu-id="e7d3f-102">Guide pratique pour supprimer une clé de Registre en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e7d3f-102">How to: Delete a Registry Key in Visual Basic</span></span>
<span data-ttu-id="e7d3f-103">Vous pouvez utiliser les méthodes<xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> et <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> pour supprimer les clés de Registre.</span><span class="sxs-lookup"><span data-stu-id="e7d3f-103">The <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> and <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> methods can be used to delete registry keys.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="e7d3f-104">Procédure</span><span class="sxs-lookup"><span data-stu-id="e7d3f-104">Procedure</span></span>  
  
#### <a name="to-delete-a-registry-key"></a><span data-ttu-id="e7d3f-105">Pour supprimer une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="e7d3f-105">To delete a registry key</span></span>  
  
-   <span data-ttu-id="e7d3f-106">Utilisez la méthode `DeleteSubKey` pour supprimer une clé de Registre.</span><span class="sxs-lookup"><span data-stu-id="e7d3f-106">Use the `DeleteSubKey` method to delete a registry key.</span></span> <span data-ttu-id="e7d3f-107">Cet exemple supprime la clé Software/TestApp dans la ruche CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="e7d3f-107">This example deletes the key Software/TestApp in the CurrentUser hive.</span></span> <span data-ttu-id="e7d3f-108">Vous pouvez spécifier la chaîne appropriée dans le code ou faire en sorte que celui-ci repose sur des informations fournies par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e7d3f-108">You can change this in the code to the appropriate string, or have it rely on user-supplied information.</span></span>  
  
     <span data-ttu-id="e7d3f-109">[!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e7d3f-109">[!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e7d3f-110">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="e7d3f-110">Robust Programming</span></span>  
 <span data-ttu-id="e7d3f-111">La méthode `DeleteSubKey` retourne une chaîne vide si la paire clé/valeur n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="e7d3f-111">The `DeleteSubKey` method returns an empty string if the key/value pair does not exist.</span></span>  
  
 <span data-ttu-id="e7d3f-112">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="e7d3f-112">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="e7d3f-113">Le nom de la clé est `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="e7d3f-113">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="e7d3f-114">L’utilisateur ne dispose pas des autorisations pour supprimer des clés de Registre (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="e7d3f-114">The user does not have permissions to delete registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="e7d3f-115">Le nom de la clé dépasse la limite de 255 caractères (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="e7d3f-115">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="e7d3f-116">La clé de Registre est en lecture seule (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="e7d3f-116">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e7d3f-117">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e7d3f-117">.NET Framework Security</span></span>  
 <span data-ttu-id="e7d3f-118">Les appels au Registre échouent quand l’utilisateur ne dispose pas des autorisations d’exécution nécessaires (<xref:System.Security.Permissions.RegistryPermission>) ou de l’accès correct (tel que déterminé par les listes de contrôle d’accès) pour créer ou écrire des paramètres.</span><span class="sxs-lookup"><span data-stu-id="e7d3f-118">Registry calls fail if either sufficient run-time permissions are not granted (<xref:System.Security.Permissions.RegistryPermission>) or if the user does not have the correct access (as determined by the ACLs) for creating or writing to settings.</span></span> <span data-ttu-id="e7d3f-119">Par exemple, une application locale qui dispose de l’autorisation de sécurité d’accès du code peut ne pas disposer des autorisations de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="e7d3f-119">For example, a local application that has the code access security permission might not have operating system permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7d3f-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7d3f-120">See Also</span></span>  
 <span data-ttu-id="e7d3f-121"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A></span><span class="sxs-lookup"><span data-stu-id="e7d3f-121"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A></span></span>   
 <span data-ttu-id="e7d3f-122"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A></span><span class="sxs-lookup"><span data-stu-id="e7d3f-122"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A></span></span>   
 <span data-ttu-id="e7d3f-123"><xref:Microsoft.Win32.RegistryKey></span><span class="sxs-lookup"><span data-stu-id="e7d3f-123"><xref:Microsoft.Win32.RegistryKey></span></span>   
 <span data-ttu-id="e7d3f-124">[Sécurité et Registre](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md) </span><span class="sxs-lookup"><span data-stu-id="e7d3f-124">[Security and the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md) </span></span>  
 [<span data-ttu-id="e7d3f-125">Lecture et écriture dans le Registre</span><span class="sxs-lookup"><span data-stu-id="e7d3f-125">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)

