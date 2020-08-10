# Location-API
API to Add and Get Location
SET
   ANSI_NULLS 
   ON 
   GO 
   SET
      QUOTED_IDENTIFIER 
      ON 
      GO alter PROCEDURE spGetLocation @SearchString nvarchar(100), @SortBy nvarchar(50), @SortOrder varchar(20) AS 
      BEGIN
         SET
            NOCOUNT 
            ON;
select
   Id,
   [Address],
   City,
   [State] 
from
   Location 
where
   [Address] like '%' + @SearchString + '%' 
   or City like '%' + @SearchString + '%' 
   or [State] like '%' + @SearchString + '%' 
order by
   case
      when
         (
            @SortBy = 'Address' 
            and @SortOrder = 'asc'
         )
      then
         [Address] 
   end
   asc, 
   case
      when
         (
            @SortBy = 'Address' 
            and @SortOrder = 'dec'
         )
      then
         [Address] 
   end
   desc, 
   case
      when
         (
            @SortBy = 'City' 
            and @SortOrder = 'asc'
         )
      then
         City 
   end
   asc, 
   case
      when
         (
            @SortBy = 'City' 
            and @SortOrder = 'dec'
         )
      then
         City 
   end
   desc, 
   case
      when
         (
            @SortBy = 'Address' 
            and @SortOrder = 'asc'
         )
      then
         [State] 
   end
   asc, 
   case
      when
         (
            @SortBy = 'Address' 
            and @SortOrder = 'dec'
         )
      then
         [State] 
   end
   desc 
      END
      GO
      
      
      
      USE [LocationDB]
GO

/****** Object:  Table [dbo].[Location]    Script Date: 8/10/2020 5:12:20 PM ******/
SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

CREATE TABLE [dbo].[Location](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[Address] [nvarchar](150) NULL,
	[City] [nvarchar](50) NULL,
	[State] [nvarchar](50) NULL,
 CONSTRAINT [PK_Location] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]

GO



