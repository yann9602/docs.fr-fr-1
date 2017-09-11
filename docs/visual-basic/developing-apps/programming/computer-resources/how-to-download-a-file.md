---
title: "Guide pratique pour télécharger un fichier en Visual Basic"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- downloading Internet resources, files
- downloading files
- remote computers, downloading from
- files, downloading
- files, transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
caps.latest.revision: 22
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
ms.openlocfilehash: 8988b922df921c2de3e2c4f6d7a8e98887ba7b0a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-download-a-file-in-visual-basic"></a><span data-ttu-id="efae7-102">Guide pratique pour télécharger un fichier en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="efae7-102">How to: Download a File in Visual Basic</span></span>
<span data-ttu-id="efae7-103">Vous pouvez utiliser la méthode <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> pour télécharger un fichier distant et le stocker à un emplacement spécifique.</span><span class="sxs-lookup"><span data-stu-id="efae7-103">The <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> method can be used to download a remote file and store it to a specific location.</span></span> <span data-ttu-id="efae7-104">Si le paramètre `ShowUI` a la valeur `True`, une boîte de dialogue s’affiche pour indiquer la progression du téléchargement et permettre aux utilisateurs d’annuler l’opération.</span><span class="sxs-lookup"><span data-stu-id="efae7-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed showing the progress of the download and allowing users to cancel the operation.</span></span> <span data-ttu-id="efae7-105">Par défaut, les fichiers existants ayant le même nom ne sont pas remplacés. Si vous souhaitez remplacer les fichiers existants, affectez la valeur `True` au paramètre `overwrite`.</span><span class="sxs-lookup"><span data-stu-id="efae7-105">By default, existing files having the same name are not overwritten; if you want to overwrite existing files, set the `overwrite` parameter to `True`.</span></span>  
  
 <span data-ttu-id="efae7-106">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="efae7-106">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="efae7-107">Le nom du lecteur n’est pas valide (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="efae7-107">Drive name is not valid (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="efae7-108">L’authentification nécessaire n’a pas été fournie (<xref:System.UnauthorizedAccessException> ou <xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="efae7-108">Necessary authentication has not been supplied (<xref:System.UnauthorizedAccessException> or <xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="efae7-109">Le serveur ne répond pas dans le délai (`connectionTimeout`) spécifié (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="efae7-109">The server does not respond within the specified `connectionTimeout` (<xref:System.TimeoutException>).</span></span>  
  
-   <span data-ttu-id="efae7-110">La demande est refusée par le site web (<xref:System.Net.WebException>).</span><span class="sxs-lookup"><span data-stu-id="efae7-110">The request is denied by the Web site (<xref:System.Net.WebException>).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
>  <span data-ttu-id="efae7-111">Ne vous basez pas sur le nom d'un fichier pour en déterminer le contenu.</span><span class="sxs-lookup"><span data-stu-id="efae7-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="efae7-112">Par exemple, le fichier Form1.vb peut ne pas être un fichier source Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="efae7-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="efae7-113">Vérifiez toutes les entrées avant d'utiliser les données dans votre application.</span><span class="sxs-lookup"><span data-stu-id="efae7-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="efae7-114">Le fichier n'a peut-être pas le contenu attendu, et les méthodes utilisées pour lire le fichier peuvent échouer.</span><span class="sxs-lookup"><span data-stu-id="efae7-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
### <a name="to-download-a-file"></a><span data-ttu-id="efae7-115">Pour télécharger un fichier</span><span class="sxs-lookup"><span data-stu-id="efae7-115">To download a file</span></span>  
  
-   <span data-ttu-id="efae7-116">Utilisez la méthode `DownloadFile` pour télécharger le fichier, en spécifiant l’emplacement du fichier cible sous forme de chaîne ou d’URI et en spécifiant l’emplacement de stockage du fichier.</span><span class="sxs-lookup"><span data-stu-id="efae7-116">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file.</span></span> <span data-ttu-id="efae7-117">Cet exemple télécharge le fichier `WineList.txt` à partir de `http://www.cohowinery.com/downloads` et l’enregistre dans `C:\Documents and Settings\All Users\Documents` :</span><span class="sxs-lookup"><span data-stu-id="efae7-117">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`:</span></span>  
  
     <span data-ttu-id="efae7-118">[!code-vb[VbResourceTasks#9](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="efae7-118">[!code-vb[VbResourceTasks#9](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_1.vb)]</span></span>  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a><span data-ttu-id="efae7-119">Pour télécharger un fichier en spécifiant un intervalle de délai d’attente</span><span class="sxs-lookup"><span data-stu-id="efae7-119">To download a file, specifying a time-out interval</span></span>  
  
-   <span data-ttu-id="efae7-120">Utilisez la méthode `DownloadFile` pour télécharger le fichier, en spécifiant l’emplacement du fichier cible sous forme de chaîne ou d’URI, en spécifiant l’emplacement de stockage du fichier et en spécifiant l’intervalle de délai d’attente en millisecondes (la valeur par défaut est 1 000).</span><span class="sxs-lookup"><span data-stu-id="efae7-120">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI, specifying the location at which to store the file, and specifying the time-out interval in milliseconds (the default is 1000).</span></span> <span data-ttu-id="efae7-121">Cet exemple télécharge le fichier `WineList.txt` à partir de `http://www.cohowinery.com/downloads` et l’enregistre dans `C:\Documents and Settings\All Users\Documents`, en spécifiant un intervalle de délai d’attente de 500 millisecondes :</span><span class="sxs-lookup"><span data-stu-id="efae7-121">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, specifying a time-out interval of 500 milliseconds:</span></span>  
  
     <span data-ttu-id="efae7-122">[!code-vb[VbResourceTasks#10](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="efae7-122">[!code-vb[VbResourceTasks#10](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_2.vb)]</span></span>  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="efae7-123">Pour télécharger un fichier en fournissant un nom d’utilisateur et un mot de passe</span><span class="sxs-lookup"><span data-stu-id="efae7-123">To download a file, supplying a user name and password</span></span>  
  
-   <span data-ttu-id="efae7-124">Utilisez la méthode `DownLoadFile` pour télécharger le fichier, en spécifiant l’emplacement du fichier cible sous forme de chaîne ou d’URI et en spécifiant l’emplacement de stockage du fichier, du nom d’utilisateur et du mot de passe.</span><span class="sxs-lookup"><span data-stu-id="efae7-124">Use the `DownLoadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file, the user name, and the password.</span></span> <span data-ttu-id="efae7-125">Cet exemple télécharge le fichier `WineList.txt` à partir de `http://www.cohowinery.com/downloads` et l’enregistre dans `C:\Documents and Settings\All Users\Documents`, avec le nom d’utilisateur `anonymous` et un mot de passe vide.</span><span class="sxs-lookup"><span data-stu-id="efae7-125">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, with the user name `anonymous` and a blank password.</span></span>  
  
     <span data-ttu-id="efae7-126">[!code-vb[VbResourceTasks#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="efae7-126">[!code-vb[VbResourceTasks#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_3.vb)]</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="efae7-127">Le protocole FTP utilisé par la méthode `DownLoadFile` envoie les informations, notamment les mots de passe, en texte brut. Il ne doit pas être utilisé pour transmettre des informations sensibles.</span><span class="sxs-lookup"><span data-stu-id="efae7-127">The FTP protocol used by the `DownLoadFile` method sends information, including passwords, in plain text and should not be used for transmitting sensitive information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efae7-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efae7-128">See Also</span></span>  
 <span data-ttu-id="efae7-129"><xref:Microsoft.VisualBasic.Devices.Network></span><span class="sxs-lookup"><span data-stu-id="efae7-129"><xref:Microsoft.VisualBasic.Devices.Network></span></span>   
 <span data-ttu-id="efae7-130"><xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A></span><span class="sxs-lookup"><span data-stu-id="efae7-130"><xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A></span></span>   
 <span data-ttu-id="efae7-131">[Guide pratique pour charger un fichier](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md) </span><span class="sxs-lookup"><span data-stu-id="efae7-131">[How to: Upload a File](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md) </span></span>  
 [<span data-ttu-id="efae7-132">Guide pratique pour analyser des chemins</span><span class="sxs-lookup"><span data-stu-id="efae7-132">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)

