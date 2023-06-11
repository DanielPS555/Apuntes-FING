```sql
select cb.codigo_barra 
from articulos_empresas ae 
	inner join codigos_barras cb on ae.art_codigo = cb.art_codigo 
where ae.emp_codigo = 1 
and not exists (
	select 1 
	from articulos_empresas a2 
	where a2.emp_codigo = 4539 
	and ae.art_codigo = a2.art_codigo
				) 
and Ae.Est_Codigo = 1 
and codigo_barra > '7730000000000'
```