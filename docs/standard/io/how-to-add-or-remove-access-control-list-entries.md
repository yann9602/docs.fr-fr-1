---
title: "Comment : ajouter ou supprimer des entrées dans la liste de contrôle d'accès"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ACEs [.NET Framework]
- ACLs [.NET Framework]
- access control entries [.NET Framework]
- I/O [.NET Framework], access control list entries
- access control lists [.NET Framework]
ms.assetid: 53758b39-bd9b-4640-bb04-cad5ed8d0abf
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 988fd354caa5fcc716107087242ead113c9a9939
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-add-or-remove-access-control-list-entries"></a>Comment : ajouter ou supprimer des entrées dans la liste de contrôle d'accès
Pour ajouter des entrées de liste de contrôle d'accès (ACL) dans un fichier, ou pour en supprimer, vous devez obtenir l'objet <xref:System.Security.AccessControl.FileSecurity> ou <xref:System.Security.AccessControl.DirectorySecurity> à partir du fichier ou du répertoire, le modifier et le réappliquer ensuite dans le fichier ou répertoire.  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-file"></a>Pour ajouter ou supprimer une entrée ACL dans un fichier  
  
1.  Appelez la méthode <xref:System.IO.File.GetAccessControl%2A> pour obtenir un objet <xref:System.Security.AccessControl.FileSecurity> contenant les entrées ACL actuelles d'un fichier.  
  
2.  Ajoutez ou supprimez des entrées ACL à partir de l'objet <xref:System.Security.AccessControl.FileSecurity> retourné à l'étape 1.  
  
3.  Passez l'objet <xref:System.Security.AccessControl.FileSecurity> à la méthode <xref:System.IO.File.SetAccessControl%2A> pour appliquer les modifications.  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-directory"></a>Pour ajouter ou supprimer une entrée ACL dans un répertoire  
  
1.  Appelez la méthode <xref:System.IO.Directory.GetAccessControl%2A> pour obtenir un objet <xref:System.Security.AccessControl.DirectorySecurity> contenant les entrées ACL actuelles d'un répertoire.  
  
2.  Ajoutez ou supprimez des entrées ACL à partir de l'objet <xref:System.Security.AccessControl.DirectorySecurity> retourné à l'étape 1.  
  
3.  Passez l'objet <xref:System.Security.AccessControl.DirectorySecurity> à la méthode <xref:System.IO.Directory.SetAccessControl%2A> pour appliquer les modifications.  
  
## <a name="example"></a>Exemple  
 [!code-cpp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/cpp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/cpp/sample.cpp#1)]
 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Vous devez entrer un compte d'utilisateur ou de groupe valide pour exécuter cet exemple. Cet exemple utilise un objet <xref:System.IO.File>, mais la même procédure vaut aussi pour les classes <xref:System.IO.FileInfo>, <xref:System.IO.Directory> et <xref:System.IO.DirectoryInfo>.
