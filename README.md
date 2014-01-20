test
====

test
seq no:

;WITH	Numbers (N) AS
		(
		SELECT	TOP (9999)
				ROW_NUMBER() OVER (ORDER BY (SELECT NULL))
		FROM	master.sys.columns
		CROSS
		JOIN	master.sys.columns C2
		)
SELECT	N
FROM	Numbers where N between 100 and 200;

---------


DBCC USEROPTIONS;

-----------------------------

get duplicate



SELECT Your_colm, COUNT(*) TotalCount
FROM Your_tbl
GROUP BY Your_colm
HAVING COUNT(*) > 1
ORDER BY COUNT(*) DESC

--------------------

;WITH	Numbers (N) AS
		(
		SELECT	TOP (9999)
				ROW_NUMBER() OVER (ORDER BY (SELECT NULL))
		FROM	master.sys.columns
		CROSS
		JOIN	master.sys.columns C2
		)
		
insert into Postcodes(id) 
SELECT	REPLICATE('0', 4 - LEN(CONVERT(VARCHAR(4), N))) + CONVERT(VARCHAR(4), N) as codes
FROM Numbers

--------------------

NextDay Mid Night

select DateAdd(day, Datediff(day, 0, getdate()) +1, 0)


YesterDay mid night:

select DateAdd(day, Datediff(day, 0, getdate()) -1, 0)


-------------------------

drop table #sequence
create table #sequence (id int not null primary key)

insert into #sequence(id) select id from PostCodes where salesunit=86

select * from #sequence

select l.id + 1 as start, min(fr.id) - 1 as stop
from #sequence as l
    left outer join #sequence as r on l.id = r.id - 1
    left outer join #sequence as fr on l.id < fr.id
where r.id is null and fr.id is not null
group by l.id, r.id;

-------------------------------

SELECT      DATEADD(YEAR, DATEDIFF(YEAR, 0,

            DATEADD(YEAR, -1, GETDATE())), 0),

            'First Day of Previous Year'

UNION ALL

SELECT      DATEADD(MILLISECOND, -3, DATEADD(YEAR,

            DATEDIFF(YEAR, 0, DATEADD(YEAR, -1, GETDATE())) + 1, 0)),

            'Last Day of Previous Year'

UNION ALL

SELECT      DATEADD(YEAR, DATEDIFF(YEAR, 0, GETDATE()), 0),

            'First Day of Current Year'

UNION ALL

SELECT      DATEADD(MILLISECOND, -3,

            DATEADD(YEAR, DATEDIFF(YEAR, 0, GETDATE()) + 1, 0)),

            'Last Day of Current Year'

UNION ALL

SELECT      DATEADD(YEAR, DATEDIFF(YEAR, 0,

            DATEADD(YEAR,1,GETDATE())), 0),

            'First Day of Next Year'

UNION ALL

SELECT      DATEADD(MILLISECOND, -3,

            DATEADD(YEAR, DATEDIFF(YEAR, 0,

            DATEADD(YEAR, 1, GETDATE())) + 1, 0)),

            'Last Day of Next Year' 

