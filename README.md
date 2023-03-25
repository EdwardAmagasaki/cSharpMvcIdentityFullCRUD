# C# Sharp MVC ASP.NET 4.8 Identity 

Vamos personalizar o nosso sistema de autenticações e autorizações do ASP.NET para que fique exatamente de acordo com a nossa campanha e alinhada com o nosso fundamento de desenvolvimento ágil.

Então a pergunta seria, que Entidades serão necessárias para a criação dessa aplicação?

O questionário de perguntas envolverá 12 títulos e 12 sub-títulos, bem como 12 imagens com a data de cadastro e o nome do grupo e do avatar relacionado.

FrontPagePosts.cs ( Modelo C# Sharp )

```
using System;
using System.ComponentModel.DataAnnotations;
using System.ComponentModel.DataAnnotations.Schema;

namespace YourNamespace
{
    public class FrontPagePostListas
    {
        [Key]
        [DatabaseGenerated(DatabaseGeneratedOption.Identity)]
        public int FrontPagePostListaId { get; set; }

        [Required]
        public int do0FrontPagePostsId { get; set; }

        [Column(TypeName = "nvarchar(4000)")]
        public string do0AvatarName { get; set; }
        
        [Column(TypeName = "nvarchar(4000)")]
        public string do0UserName { get; set; }

        [Required]
        public bool Rascunho { get; set; }

        [Column(TypeName = "nvarchar(4000)")]
        public string Autor { get; set; }

        public DateTime? Data { get; set; }

        [Column(TypeName = "nvarchar(4000)")]
        public string Titulo { get; set; }

        [Column(TypeName = "nvarchar(200)")]
        public string Introducao { get; set; }

        [Column(TypeName = "nvarchar(4000)")]
        public string Descricao { get; set; }

        [Column(TypeName = "nvarchar(4000)")]
        public string Pasta { get; set; }

        [Required]
        public bool LinkExterno { get; set; }

        [Column(TypeName = "nvarchar(4000)")]
        public string LinkUrl { get; set; }

        [Required]
        public bool Reserva1 { get; set; }

        [ForeignKey("do0FrontPagePostsId")]
        public virtual FrontPagePosts FrontPagePosts { get; set; }
    }
}

```
Please note the following details about the conversion:

The class name is FrontPagePostListas based on the table name.
Each column in the table has been converted to a property in the C# class with the appropriate data type and constraints.
The primary key constraint is implemented using the [Key] attribute.
For the identity column, we use the [DatabaseGenerated(DatabaseGeneratedOption.Identity)] attribute.
Foreign key constraint is created by adding [ForeignKey("do0FrontPagePostsId")] attribute and defining virtual reference via public virtual FrontPagePosts FrontPagePosts { get; set; }.
Attributes like [Column(TypeName = "nvarchar(4000)")] have been used to define the data type of columns which do not match a typical C# data type.

Sub-Título - FrontPagePostListas.cs  ( Modelo C# Sharp )

```
CREATE TABLE [FrontPagePostListas] (
  [FrontPagePostListaId] int IDENTITY (1,1) NOT NULL
, [do0FrontPagePostsId] int NOT NULL
, [do0AvatarName] nvarchar(4000) NULL
, [do0UserName] nvarchar(4000) NULL
, [Rascunho] bit NOT NULL
, [Autor] nvarchar(4000) NULL
, [Data] datetime NULL
, [Titulo] nvarchar(4000) NULL
, [Introducao] nvarchar(200) NULL
, [Descricao] nvarchar(4000) NULL
, [Pasta] nvarchar(4000) NULL
, [LinkExterno] bit NOT NULL
, [LinkUrl] nvarchar(4000) NULL
, [Reserva1] bit NOT NULL
);
GO
ALTER TABLE [FrontPagePostListas] ADD CONSTRAINT [PK_dbo.FrontPagePostListas] PRIMARY KEY ([FrontPagePostListaId]);
GO
CREATE INDEX [IX_do0FrontPagePostsId] ON [FrontPagePostListas] ([do0FrontPagePostsId] ASC);
GO
ALTER TABLE [FrontPagePostListas] ADD CONSTRAINT [FK_dbo.FrontPagePostListas_dbo.FrontPagePosts_do0FrontPagePostsId] FOREIGN KEY ([do0FrontPagePostsId]) REFERENCES [FrontPagePosts]([do0FrontPagePostsId]) ON DELETE CASCADE ON UPDATE NO ACTION;
GO
```

FrontPagePosts.cs ( Modelo C# Sharp )

```
CREATE TABLE [FrontPagePosts] (
  [do0FrontPagePostsId] int IDENTITY (1,1) NOT NULL
, [do0AvatarName] nvarchar(4000) NULL
, [do0UserName] nvarchar(4000) NULL
, [Rascunho] bit NOT NULL
, [Autor] nvarchar(4000) NULL
, [Data] datetime NULL
, [Titulo] nvarchar(4000) NULL
, [Introducao] nvarchar(200) NULL
, [Descricao] nvarchar(4000) NULL
, [Pasta] nvarchar(4000) NULL
, [LinkExterno] bit NOT NULL
, [LinkUrl] nvarchar(4000) NULL
, [Reserva1] bit NOT NULL
);
GO
ALTER TABLE [FrontPagePosts] ADD CONSTRAINT [PK_dbo.FrontPagePosts] PRIMARY KEY ([do0FrontPagePostsId]);
GO
```
Sub-Título - FrontPagePostListas.cs  ( Modelo C# Sharp )

```
public class FrontPagePostListas
{
    public int FrontPagePostListaId { get; set; }
    public int do0FrontPagePostsId { get; set; }
    public string do0AvatarName { get; set; }
    public string do0UserName { get; set; }
    public bool Rascunho { get; set; }
    public string Autor { get; set; }
    public DateTime? Data { get; set; }
    public string Titulo { get; set; }
    public string Introducao { get; set; }
    public string Descricao { get; set; }
    public string Pasta { get; set; }
    public bool LinkExterno { get; set; }
    public string LinkUrl { get; set; }
    public bool Reserva1 { get; set; }
}
```
This C# class defines all the fields of the FrontPagePostListas table, with the same names and data types. The int and bool values are automatically non-nullable, while string and DateTime values are nullable by default, and therefore, they needed a question mark symbol in the declaration to make them nullable.


O que poderá ser vinculádo de forma opcional? 

1. Vídeo Youtube
2. Link Externo
3. Midia Externa
4. Telegram
5. Twitter
6. Chat GPT
7. Mídia Instragram
8. Mídia Pinterinterest
9. E-Mail
10. 