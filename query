CREATE TABLE `rakamin-kf-analytics01.kimia_farma.analisa` AS
SELECT 
  transaction_id,
  date,
  ft.branch_id,
  branch_name,
  kota,
  provinsi,
  kc.rating as rating_cabang,
  customer_name,
  ft.product_id,
  product_name,
  p.price as actual_price,
  discount_percentage,
  case 
      when ft.price <= 50000 then "10%"
      when ft.price between 50001 and 100000 then "15%"
      when ft.price between 100001 and 300000 then "20%"  
      when ft.price between 300001 and 500000 then "25%" 
      when ft.price > 500000 then "30%"
      end as persentase_gross_laba,
  p.price - (p.price * discount_percentage) as nett_sales,
  (p.price - (p.price * ft.discount_percentage)) * 
        CASE 
            when ft.price <= 50000 then 0.1
            when ft.price between 50001 and 100000 then 0.15 
            when ft.price between 100001 and 300000 then 0.2  
            when ft.price between 300001 and 500000 then 0.25  
            when ft.price > 500000 then 0.3
        END AS nett_profit,
  ft.rating as rating_transaksi
  

  FROM  `rakamin-academy001.Rakamin.kf_final_transaction` as ft 

  LEFT JOIN `rakamin-academy001.Rakamin.kf_kantor_cabang` as kc
  ON ft.branch_id = kc.branch_id
  LEFT JOIN `rakamin-academy001.Rakamin.kf_product` as p
  ON ft.product_id = p.product_id
