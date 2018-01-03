---
title: "Données FILESTREAM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 77d6dbafc5a7c3afd9998fd8e9ae54ce60f90a45
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="filestream-data"></a><span data-ttu-id="8b4cf-102">Données FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="8b4cf-102">FILESTREAM Data</span></span>
<span data-ttu-id="8b4cf-103">L'attribut de stockage FILESTREAM est destiné aux données binaires (BLOB) stockées dans une colonne varbinary(max).</span><span class="sxs-lookup"><span data-stu-id="8b4cf-103">The FILESTREAM storage attribute is for binary (BLOB) data stored in a varbinary(max) column.</span></span> <span data-ttu-id="8b4cf-104">Avant l'introduction de cet attribut, le stockage des données binaires nécessitait un traitement spécial.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-104">Before FILESTREAM, storing binary data required special handling.</span></span> <span data-ttu-id="8b4cf-105">Les données non structurées, telles que les documents texte, les images et les vidéos, sont souvent stockées en dehors de la base de données, ce qui rend difficile leur gestion.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-105">Unstructured data, such as text documents, images and video, is often stored outside of the database, making it difficult to manage.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b4cf-106">Vous devez installer le .NET Framework 3.5 SP1 (ou version ultérieure) pour utiliser les données FILESTREAM avec SqlClient.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-106">You must install the .NET Framework 3.5 SP1 (or later) to work with FILESTREAM data using SqlClient.</span></span>  
  
 <span data-ttu-id="8b4cf-107">Si vous spécifiez l'attribut FILESTREAM sur une colonne varbinary(max), [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] stocke les données sur le système de fichiers NTFS local au lieu du fichier de base de données.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-107">Specifying the FILESTREAM attribute on a varbinary(max) column causes [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] to store the data on the local NTFS file system instead of in the database file.</span></span> <span data-ttu-id="8b4cf-108">Même si elles sont stockées séparément, vous pouvez utiliser les mêmes instructions [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] prises en charge pour l'utilisation des données varbinary(max) stockées dans la base.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-108">Although it is stored separately, you can use the same [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statements that are supported for working with varbinary(max) data that is stored in the database.</span></span>  
  
## <a name="sqlclient-support-for-filestream"></a><span data-ttu-id="8b4cf-109">Prise en charge de SqlClient pour FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="8b4cf-109">SqlClient Support for FILESTREAM</span></span>  
 <span data-ttu-id="8b4cf-110">Le fournisseur de données  [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] pour [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], <xref:System.Data.SqlClient>, prend en charge la lecture et l'écriture vers les données FILESTREAM en utilisant la classe <xref:System.Data.SqlTypes.SqlFileStream> définie dans l'espace de noms <xref:System.Data.SqlTypes>.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-110">The [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Data Provider for [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], <xref:System.Data.SqlClient>, supports reading and writing to FILESTREAM data using the <xref:System.Data.SqlTypes.SqlFileStream> class defined in the <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="8b4cf-111">`SqlFileStream` hérite de la classe <xref:System.IO.Stream>, qui fournit les méthodes permettant de lire et d'écrire vers les flux de données.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-111">`SqlFileStream` inherits from the <xref:System.IO.Stream> class, which provides methods for reading and writing to streams of data.</span></span> <span data-ttu-id="8b4cf-112">La lecture à partir d'un flux transfère les données du flux dans une structure de données, tel qu'un tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-112">Reading from a stream transfers data from the stream into a data structure, such as an array of bytes.</span></span> <span data-ttu-id="8b4cf-113">L'écriture transfère les données de la structure dans un flux.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-113">Writing transfers the data from the data structure into a stream.</span></span>  
  
### <a name="creating-the-includessnoversionincludesssnoversion-mdmd-table"></a><span data-ttu-id="8b4cf-114">Création de la table [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b4cf-114">Creating the [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Table</span></span>  
 <span data-ttu-id="8b4cf-115">L'instruction [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] suivante crée une table nommée employees et y insère une ligne de données.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-115">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statements creates a table named employees and inserts a row of data.</span></span> <span data-ttu-id="8b4cf-116">Après avoir activé le stockage FILESTREAM, vous pouvez combiner cette table aux exemples de code suivants.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-116">Once you have enabled FILESTREAM storage, you can use this table in conjunction with the code examples that follow.</span></span> <span data-ttu-id="8b4cf-117">Les liens vers les ressources dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-117">The links to resources in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online are located at the end of this topic.</span></span>  
  
```  
CREATE TABLE employees  
(  
  EmployeeId INT  NOT NULL  PRIMARY KEY,  
  Photo VARBINARY(MAX) FILESTREAM  NULL,  
  RowGuid UNIQUEIDENTIFIER  NOT NULL  ROWGUIDCOL  
  UNIQUE DEFAULT NEWID()  
)  
GO  
Insert into employees  
Values(1, 0x00, default)  
GO  
```  
  
### <a name="example-reading-overwriting-and-inserting-filestream-data"></a><span data-ttu-id="8b4cf-118">Exemple : lecture, remplacement et insertion de données FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="8b4cf-118">Example: Reading, Overwriting, and Inserting FILESTREAM Data</span></span>  
 <span data-ttu-id="8b4cf-119">L'exemple suivant montre comment lire les données à partir d'un fichier FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-119">The following sample demonstrates how to read data from a FILESTREAM.</span></span> <span data-ttu-id="8b4cf-120">Le code obtient le chemin d'accès logique au fichier, en affectant la valeur `FileAccess` à `Read` et la valeur `FileOptions` à `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-120">The code gets the logical path to the file, setting the `FileAccess` to `Read` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="8b4cf-121">Puis le code lit les octets à partir du SqlFileStream dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-121">The code then reads the bytes from the SqlFileStream into the buffer.</span></span> <span data-ttu-id="8b4cf-122">Les octets s'affichent ensuite dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-122">The bytes are then written to the console window.</span></span>  
  
 <span data-ttu-id="8b4cf-123">Cet exemple montre également comment écrire des données dans un fichier FILESTREAM dans lequel toutes les données existantes sont remplacées.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-123">The sample also demonstrates how to write data to a FILESTREAM in which all existing data is overwritten.</span></span> <span data-ttu-id="8b4cf-124">Le code obtient le chemin d'accès logique au fichier et crée l'élément `SqlFileStream`, en affectant la valeur `FileAccess` à `Write` et la valeur `FileOptions` à `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-124">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `Write` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="8b4cf-125">Un seul octet est écrit dans le `SqlFileStream`, remplaçant ainsi les données du fichier.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-125">A single byte is written to the `SqlFileStream`, replacing any data in the file.</span></span>  
  
 <span data-ttu-id="8b4cf-126">L'exemple également montre comment écrire des données dans un fichier FILESTREAM en utilisant la méthode Seek pour ajouter des données à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-126">The sample also demonstrates how to write data to a FILESTREAM by using the Seek method to append data to the end of the file.</span></span> <span data-ttu-id="8b4cf-127">Le code obtient le chemin d'accès logique au fichier et crée le `SqlFileStream`, en affectant la valeur `FileAccess` à `ReadWrite` et la valeur `FileOptions` à `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-127">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `ReadWrite` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="8b4cf-128">Le code utilise la méthode Seek pour ajouter un seul octet à la fin du fichier existant.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-128">The code uses the Seek method to seek to the end of the file, appending a single byte to the existing file.</span></span>  
  
```csharp  
using System;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Data;  
using System.IO;  
  
namespace FileStreamTest  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder("server=(local);integrated security=true;database=myDB");  
            ReadFilestream(builder);  
            OverwriteFilestream(builder);  
            InsertFilestream(builder);  
  
            Console.WriteLine("Done");  
        }  
  
        private static void ReadFilestream(SqlConnectionStringBuilder connStringBuilder)  
        {  
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))  
            {  
                connection.Open();  
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);  
  
                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);  
                command.Transaction = tran;  
  
                using (SqlDataReader reader = command.ExecuteReader())  
                {  
                    while (reader.Read())  
                    {  
                        // Get the pointer for the file  
                        string path = reader.GetString(0);  
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
                        // Create the SqlFileStream  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Read, FileOptions.SequentialScan, allocationSize: 0))  
                        {  
                            // Read the contents as bytes and write them to the console  
                            for (long index = 0; index < fileStream.Length; index++)  
                            {  
                                Console.WriteLine(fileStream.ReadByte());  
                            }  
                        }  
                    }  
                }  
                tran.Commit();  
            }  
        }  
  
        private static void OverwriteFilestream(SqlConnectionStringBuilder connStringBuilder)  
        {  
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))  
            {  
                connection.Open();  
  
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);  
  
                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);  
                command.Transaction = tran;  
  
                using (SqlDataReader reader = command.ExecuteReader())  
                {  
                    while (reader.Read())  
                    {  
                        // Get the pointer for file   
                        string path = reader.GetString(0);  
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
                        // Create the SqlFileStream  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))  
                        {  
                            // Write a single byte to the file. This will  
                            // replace any data in the file.  
                            fileStream.WriteByte(0x01);  
                        }  
                    }  
                }  
                tran.Commit();  
            }  
        }  
  
        private static void InsertFilestream(SqlConnectionStringBuilder connStringBuilder)  
        {  
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))  
            {  
                connection.Open();  
  
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);  
  
                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);  
                command.Transaction = tran;  
  
                using (SqlDataReader reader = command.ExecuteReader())  
                {  
                    while (reader.Read())  
                    {  
                        // Get the pointer for file  
                        string path = reader.GetString(0);  
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))  
                        {  
                            // Seek to the end of the file  
                            fileStream.Seek(0, SeekOrigin.End);  
  
                            // Append a single byte   
                            fileStream.WriteByte(0x01);  
                        }  
                    }  
                }  
                tran.Commit();  
            }  
  
        }  
    }  
} using (SqlConnection connection = new SqlConnection(  
    connStringBuilder.ToString()))  
{  
    connection.Open();  
  
    SqlCommand command = new SqlCommand("", connection);  
    command.CommandText = "select Top(1) Photo.PathName(), "  
    + "GET_FILESTREAM_TRANSACTION_CONTEXT () from employees";  
  
    SqlTransaction tran = connection.BeginTransaction(  
        System.Data.IsolationLevel.ReadCommitted);  
    command.Transaction = tran;  
  
    using (SqlDataReader reader = command.ExecuteReader())  
    {  
        while (reader.Read())  
        {  
            // Get the pointer for file  
            string path = reader.GetString(0);  
            byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
            FileStream fileStream = new SqlFileStream(path,  
                (byte[])reader.GetValue(1),  
                FileAccess.ReadWrite,  
                FileOptions.SequentialScan, 0);  
  
            // Seek to the end of the file  
            fs.Seek(0, SeekOrigin.End);  
  
            // Append a single byte   
            fileStream.WriteByte(0x01);  
            fileStream.Close();  
        }  
    }  
    tran.Commit();  
}  
```  
  
 <span data-ttu-id="8b4cf-129">Pour un autre exemple, consultez [comment stocker et extraire les données binaires dans une colonne de flux de fichier](http://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span><span class="sxs-lookup"><span data-stu-id="8b4cf-129">For another sample, see [How to store and fetch binary data into a file stream column](http://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span></span>  
  
## <a name="resources-in-includessnoversionincludesssnoversion-mdmd-books-online"></a><span data-ttu-id="8b4cf-130">Ressources dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8b4cf-130">Resources in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online</span></span>  
 <span data-ttu-id="8b4cf-131">La documentation complète relative à FILESTREAM se trouve dans les sections suivantes de la documentation en ligne de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8b4cf-131">The complete documentation for FILESTREAM is located in the following sections in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
|<span data-ttu-id="8b4cf-132">Rubrique</span><span class="sxs-lookup"><span data-stu-id="8b4cf-132">Topic</span></span>|<span data-ttu-id="8b4cf-133">Description</span><span class="sxs-lookup"><span data-stu-id="8b4cf-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8b4cf-134">[Conception et implémentation du stockage FILESTREAM](http://msdn2.microsoft.com/library/bb895234\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="8b4cf-134">[Designing and Implementing FILESTREAM Storage](http://msdn2.microsoft.com/library/bb895234\(SQL.105\).aspx)</span></span>|<span data-ttu-id="8b4cf-135">Fournit des liens vers la documentation relative à FILESTREAM et les rubriques connexes.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-135">Provides links to FILESTREAM documentation and related topics.</span></span>|  
|<span data-ttu-id="8b4cf-136">[Vue d’ensemble FILESTREAM](http://msdn2.microsoft.com/library/bb933993\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="8b4cf-136">[FILESTREAM Overview](http://msdn2.microsoft.com/library/bb933993\(SQL.105\).aspx)</span></span>|<span data-ttu-id="8b4cf-137">Explique quand utiliser le stockage FILESTREAM et comment il intègre le moteur de base de données SQL Server avec un système de fichiers NTFS.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-137">Describes when to use FILESTREAM storage and how it integrates the SQL Server Database Engine with an NTFS file system.</span></span>|  
|<span data-ttu-id="8b4cf-138">[Mise en route du stockage FILESTREAM](http://msdn.microsoft.com/library/bb933995\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="8b4cf-138">[Getting Started with FILESTREAM Storage](http://msdn.microsoft.com/library/bb933995\(SQL.105\).aspx)</span></span>|<span data-ttu-id="8b4cf-139">Explique comment activer FILESTREAM sur une instance de SQL Server, comment créer une base de données et une table pour stocker les données FILESTREAM, et comment manipuler les lignes contenant des données FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-139">Describes how to enable FILESTREAM on an instance of SQL Server, how to create a database and a table to stored FILESTREAM data, and how to manipulate rows containing FILESTREAM data.</span></span>|  
|<span data-ttu-id="8b4cf-140">[Utilisation du stockage FILESTREAM dans les Applications clientes](http://msdn.microsoft.com/library/bb933877\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="8b4cf-140">[Using FILESTREAM Storage in Client Applications](http://msdn.microsoft.com/library/bb933877\(SQL.105\).aspx)</span></span>|<span data-ttu-id="8b4cf-141">Décrit les fonctions API Win32 pour une utilisation avec des données FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-141">Describes the Win32 API functions for working with FILESTREAM data.</span></span>|  
|<span data-ttu-id="8b4cf-142">[FILESTREAM et autres fonctionnalités SQL Server](http://msdn.microsoft.com/library/bb895334\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="8b4cf-142">[FILESTREAM and Other SQL Server Features](http://msdn.microsoft.com/library/bb895334\(SQL.105\).aspx)</span></span>|<span data-ttu-id="8b4cf-143">Fournit des considérations, indications et limitations relatives à l’utilisation des données FILESTREAM avec d’autres fonctionnalités de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8b4cf-143">Provides considerations, guidelines and limitations for using FILESTREAM data with other features of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b4cf-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b4cf-144">See Also</span></span>  
 [<span data-ttu-id="8b4cf-145">Types de données SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8b4cf-145">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="8b4cf-146">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8b4cf-146">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="8b4cf-147">Sécurité d’accès du code et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8b4cf-147">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [<span data-ttu-id="8b4cf-148">Données binaires et de valeur élevée SQL Server</span><span class="sxs-lookup"><span data-stu-id="8b4cf-148">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="8b4cf-149">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="8b4cf-149">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
