---
title: "Guide pratique pour supprimer une clé de Registre en Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.DeleteSetting
helpviewer_keywords:
- GetSetting function [Visual Basic]
- registry [Visual Basic], deleting values
- GetAllSettings function
- registry keys [Visual Basic], deleting
- registry [Visual Basic], deleting keys
- examples [Visual Basic], registry
ms.assetid: ab9aca0e-42b0-4ff7-8ff9-845a4bfdf9f2
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0cb98c02531bac133b9dc37a92f75d5c0418dc7c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a><span data-ttu-id="de470-102">Guide pratique pour supprimer une clé de Registre en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="de470-102">How to: Delete a Registry Key in Visual Basic</span></span>
<span data-ttu-id="de470-103">Vous pouvez utiliser les méthodes<xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> et <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> pour supprimer les clés de Registre.</span><span class="sxs-lookup"><span data-stu-id="de470-103">The <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> and <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> methods can be used to delete registry keys.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="de470-104">Procédure</span><span class="sxs-lookup"><span data-stu-id="de470-104">Procedure</span></span>  
  
#### <a name="to-delete-a-registry-key"></a><span data-ttu-id="de470-105">Pour supprimer une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="de470-105">To delete a registry key</span></span>  
  
-   <span data-ttu-id="de470-106">Utilisez la méthode `DeleteSubKey` pour supprimer une clé de Registre.</span><span class="sxs-lookup"><span data-stu-id="de470-106">Use the `DeleteSubKey` method to delete a registry key.</span></span> <span data-ttu-id="de470-107">Cet exemple supprime la clé Software/TestApp dans la ruche CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="de470-107">This example deletes the key Software/TestApp in the CurrentUser hive.</span></span> <span data-ttu-id="de470-108">Vous pouvez spécifier la chaîne appropriée dans le code ou faire en sorte que celui-ci repose sur des informations fournies par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="de470-108">You can change this in the code to the appropriate string, or have it rely on user-supplied information.</span></span>  
  
     [!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="de470-109">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="de470-109">Robust Programming</span></span>  
 <span data-ttu-id="de470-110">La méthode `DeleteSubKey` retourne une chaîne vide si la paire clé/valeur n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="de470-110">The `DeleteSubKey` method returns an empty string if the key/value pair does not exist.</span></span>  
  
 <span data-ttu-id="de470-111">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="de470-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="de470-112">Le nom de la clé est `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="de470-112">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="de470-113">L’utilisateur ne dispose pas des autorisations pour supprimer des clés de Registre (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="de470-113">The user does not have permissions to delete registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="de470-114">Le nom de la clé dépasse la limite de 255 caractères (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="de470-114">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="de470-115">La clé de Registre est en lecture seule (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="de470-115">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="de470-116">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="de470-116">.NET Framework Security</span></span>  
 <span data-ttu-id="de470-117">Les appels au Registre échouent quand l’utilisateur ne dispose pas des autorisations d’exécution nécessaires (<xref:System.Security.Permissions.RegistryPermission>) ou de l’accès correct (tel que déterminé par les listes de contrôle d’accès) pour créer ou écrire des paramètres.</span><span class="sxs-lookup"><span data-stu-id="de470-117">Registry calls fail if either sufficient run-time permissions are not granted (<xref:System.Security.Permissions.RegistryPermission>) or if the user does not have the correct access (as determined by the ACLs) for creating or writing to settings.</span></span> <span data-ttu-id="de470-118">Par exemple, une application locale qui dispose de l’autorisation de sécurité d’accès du code peut ne pas disposer des autorisations de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="de470-118">For example, a local application that has the code access security permission might not have operating system permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de470-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de470-119">See Also</span></span>  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>  
 <xref:Microsoft.Win32.RegistryKey>  
 [<span data-ttu-id="de470-120">Sécurité et Registre</span><span class="sxs-lookup"><span data-stu-id="de470-120">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 [<span data-ttu-id="de470-121">Lecture et écriture dans le Registre</span><span class="sxs-lookup"><span data-stu-id="de470-121">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
