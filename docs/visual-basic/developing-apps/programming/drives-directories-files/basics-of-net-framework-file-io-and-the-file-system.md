---
title: "Concepts de base du syst&#232;me de fichiers et des E/S de fichier du .NET Framework (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "accès aux fichiers, E/S de fichier dans Visual Basic"
  - "attributs de fichiers, détermination"
  - "flux, opérations fondamentales"
  - "autorisations fichier"
  - "flux"
  - "flux, définition"
ms.assetid: 49d837c0-cf28-416f-8606-4d83d7b479ef
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Concepts de base du syst&#232;me de fichiers et des E/S de fichier du .NET Framework (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Les classes de l’espace de noms <xref:System.IO> sont utilisées pour travailler avec les lecteurs, les fichiers et les répertoires.  
  
 L’espace de noms <xref:System.IO> contient les classes <xref:System.IO.File> et <xref:System.IO.Directory>, qui fournissent la fonctionnalité [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] permettant de manipuler des fichiers et des répertoires. Les méthodes de ces objets étant des membres statiques ou partagés, vous pouvez les utiliser directement sans créer d’abord une instance de la classe. Les classes <xref:System.IO.FileInfo> et <xref:System.IO.DirectoryInfo>, bien connues des utilisateurs de la fonctionnalité `My`, sont associées à ces classes. Pour utiliser ces classes, vous devez qualifier complètement les noms ou importer les espaces de noms appropriés en incluant les instructions `Imports` au début du code affecté. Pour plus d’informations, consultez [Instruction Imports (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
> [!NOTE]
>  Les autres rubriques de cette section utilisent l’objet `My.Computer.FileSystem` au lieu des classes `System.IO` pour travailler avec des lecteurs, des fichiers et des répertoires. L’objet `My.Computer.FileSystem` est destiné principalement à une utilisation dans des programmes [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]. Les classes `System.IO` sont destinées à tout langage qui prend en charge le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)], notamment [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## <a name="definition-of-a-stream"></a>Définition d’un flux  
 Le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] utilise des flux pour prendre en charge la lecture et l’écriture dans des fichiers. Vous pouvez considérer un flux comme un ensemble unidimensionnel de données contiguës, ayant un début et une fin, et où le curseur indique la position actuelle dans le flux.  
  
 ![Le curseur montre la position actuelle dans FileStream.](../../../../visual-basic/developing-apps/programming/drives-directories-files/media/filestream.gif "FileStream")  
  
## <a name="stream-operations"></a>Opérations de flux  
 Les données contenues dans le flux peuvent provenir de la mémoire, d’un fichier ou d’un socket TCP/IP. Des opérations fondamentales peuvent être appliquées aux flux :  
  
-   Lecture. Vous pouvez lire à partir d’un flux, autrement dit transférer des données du flux vers une structure de données, telle qu’une chaîne ou un tableau d’octets.  
  
-   **Écriture**. Vous pouvez écrire dans un flux, autrement dit transférer des données d’une source de données vers le flux.  
  
-   **Recherche**. Vous pouvez interroger et modifier votre position dans le flux.  
  
 Pour plus d'informations, consultez [Composing Streams](../Topic/Composing%20Streams.md).  
  
## <a name="types-of-streams"></a>Types de flux  
 Dans le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)], un flux est représenté par la classe <xref:System.IO.Stream>, qui forme la classe abstraite pour tous les autres flux. Vous ne pouvez pas créer directement une instance de la classe <xref:System.IO.Stream>. Vous devez utiliser une des classes qu’elle implémente.  
  
 Il existe de nombreux types de flux, mais dans le cadre de l’utilisation des entrées/sorties (E/S) de fichiers, les types les plus importants sont la classe <xref:System.IO.FileStream> qui permet de lire et d’écrire dans des fichiers, et la classe <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> qui permet de créer des fichiers et des répertoires dans un stockage isolé. Voici d’autres flux qui peuvent être utilisés avec les E/S de fichiers :  
  
-   <xref:System.IO.BufferedStream>  
  
-   <xref:System.Security.Cryptography.CryptoStream>  
  
-   <xref:System.IO.MemoryStream>  
  
-   <xref:System.Net.Sockets.NetworkStream>.  
  
 Le tableau suivant répertorie les tâches couramment accomplies avec un flux :  
  
|||  
|-|-|  
|Pour|Voir|  
|Lire et écrire dans un fichier de données|[Comment : lire et écrire dans un fichier de données créé récemment](../Topic/How%20to:%20Read%20and%20Write%20to%20a%20Newly%20Created%20Data%20File.md)|  
|Lire le texte d’un fichier|[Comment : lire du texte dans un fichier](../Topic/How%20to:%20Read%20Text%20from%20a%20File.md)|  
|Écrire du texte dans un fichier|[Comment : écrire du texte dans un fichier](../Topic/How%20to:%20Write%20Text%20to%20a%20File.md)|  
|Lire les caractères d’une chaîne|[Comment : lire les caractères d’une chaîne](../Topic/How%20to:%20Read%20Characters%20from%20a%20String.md)|  
|Écrire des caractères dans une chaîne|[Comment : écrire des caractères dans une chaîne](../Topic/How%20to:%20Write%20Characters%20to%20a%20String.md)|  
|Chiffrer des données|[Chiffrement de données](../Topic/Encrypting%20Data.md)|  
|Déchiffrer des données|[Déchiffrement de données](../Topic/Decrypting%20Data.md)|  
  
## <a name="file-access-and-attributes"></a>Accès aux fichiers et attributs  
 Vous pouvez contrôler la façon dont les fichiers sont créés, ouverts et partagés avec les énumérations <xref:System.IO.FileAccess>, <xref:System.IO.FileMode> et <xref:System.IO.FileShare>, qui contiennent les indicateurs utilisés par les constructeurs de la classe <xref:System.IO.FileStream>. Par exemple, quand vous ouvrez ou créez un <xref:System.IO.FileStream>, l’énumération <xref:System.IO.FileMode> vous permet de spécifier si le fichier est ouvert en ajout, si un fichier est créé si le fichier spécifié n’existe pas, si le fichier est remplacé, et ainsi de suite.  
  
 L’énumération <xref:System.IO.FileAttributes> vous permet de recueillir des informations propres au fichier. L’énumération <xref:System.IO.FileAttributes> retourne les attributs stockés du fichier, par exemple s’il est compressé, chiffré, caché, en lecture seule, s’il s’agit d’une archive, d’un répertoire, d’un fichier système ou d’un fichier temporaire.  
  
 Le tableau suivant répertorie les tâches qui impliquent l’accès aux fichiers et les attributs de fichiers :  
  
|||  
|-|-|  
|**Pour**|**Consultez**|  
|Ouvrir un fichier journal et y ajouter du texte|[Comment : ouvrir un fichier journal et y ajouter des éléments](../Topic/How%20to:%20Open%20and%20Append%20to%20a%20Log%20File.md)|  
|Déterminer les attributs d’un fichier|<xref:System.IO.FileAttributes>|  
  
## <a name="file-permissions"></a>Autorisations de fichiers  
 Vous pouvez contrôler l’accès aux fichiers et aux répertoires avec la classe <xref:System.Security.Permissions.FileIOPermission>. Cela peut être particulièrement important pour les développeurs qui travaillent avec les Web Forms, qui par défaut s’exécutent dans le contexte d’un compte d’utilisateur local spécial nommé ASPNET, créé dans le cadre des installations de [!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] et [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] . Quand une telle application demande l’accès à une ressource, le compte d’utilisateur ASPNET dispose d’autorisations limitées, ce qui peut empêcher l’utilisateur d’effectuer des actions telles que l’écriture dans un fichier à partir d’une application web. Pour plus d’informations, consultez [Autorisations de sécurité](http://msdn.microsoft.com/fr-fr/b03757b4-e926-4196-b738-3733ced2bda0) et <xref:System.Security.Permissions.FileIOPermission>.  
  
## <a name="isolated-file-storage"></a>Stockage de fichiers isolé  
 Le stockage isolé est une tentative de résolution des problèmes créés lors de l’utilisation de fichiers, quand l’utilisateur ou le code n’a pas les autorisations nécessaires. Le stockage isolé assigne à chaque utilisateur un compartiment de données qui peut contenir un ou plusieurs magasins. Les magasins peuvent être isolés les uns des autres par utilisateur et par assembly. Seul l’utilisateur et l’assembly ayant créé un magasin y ont accès. Un magasin se comporte comme un système de fichiers virtuel complet : vous pouvez y créer et y manipuler des fichiers et des répertoires.  
  
 Le tableau suivant répertorie les tâches couramment associées au stockage de fichiers isolé.  
  
|||  
|-|-|  
|Pour|Voir|  
|Créer un magasin isolé|[Obtention de magasins](../Topic/How%20to:%20Obtain%20Stores%20for%20Isolated%20Storage.md)|  
|Énumérer les magasins isolés|[Énumération de magasins](../Topic/How%20to:%20Enumerate%20Stores%20for%20Isolated%20Storage.md)|  
|Supprimer un magasin isolé|[Suppression de magasins](../Topic/How%20to:%20Delete%20Stores%20in%20Isolated%20Storage.md)|  
|Créer un fichier ou un répertoire dans un stockage isolé|[Comment : créer des fichiers et des répertoires dans un stockage isolé](../Topic/How%20to:%20Create%20Files%20and%20Directories%20in%20Isolated%20Storage.md)|  
|Rechercher un fichier dans un stockage isolé|[Comment : rechercher des fichiers et des répertoires existants dans un stockage isolé](../Topic/How%20to:%20Find%20Existing%20Files%20and%20Directories%20in%20Isolated%20Storage.md)|  
|Lire ou écrire dans un fichier dans un stockage isolé|[Lecture et écriture dans des fichiers](../Topic/How%20to:%20Read%20and%20Write%20to%20Files%20in%20Isolated%20Storage.md)|  
|Supprimer un fichier ou un répertoire dans un stockage isolé|[Comment : supprimer des fichiers et des répertoires dans un stockage isolé](../Topic/How%20to:%20Delete%20Files%20and%20Directories%20in%20Isolated%20Storage.md)|  
  
## <a name="file-events"></a>Événements de fichiers  
 Le composant <xref:System.IO.FileSystemWatcher> vous permet de détecter les modifications dans les fichiers et répertoires de votre système ou sur n’importe quel ordinateur auquel vous avez accès par le biais du réseau. Par exemple, si un fichier est modifié, vous souhaiterez peut-être envoyer à un utilisateur une alerte signalant la modification. Quand des modifications se produisent, un ou plusieurs événements sont déclenchés, stockés dans une mémoire tampon et transmis au composant <xref:System.IO.FileSystemWatcher> pour traitement.  
  
## <a name="see-also"></a>Voir aussi  
 [Composition de flux](../Topic/Composing%20Streams.md)   
 [Fichier et flux de données E/S](../Topic/File%20and%20Stream%20I-O.md)   
 [E/S sur fichier asynchrones](../Topic/Asynchronous%20File%20I-O.md)   
 [Classes utilisées dans les E/S de fichier du .NET Framework et le système de fichiers (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/classes-used-in-net-framework-file-io-and-the-file-system.md)