<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>فيصل للسبوع والمناسبات - طنطا</title>
<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700;800&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:'Cairo',sans-serif}
body{background:#fffaf7;color:#222;line-height:1.6}
header{position:sticky;top:0;z-index:100;background:#fff;border-bottom:2px solid #fed7aa;display:flex;justify-content:space-between;align-items:center;padding:12px 4%}
.logo{font-weight:800;font-size:19px;color:#7c2d12}
.logo span{color:#ea580c}
.shipping-bar{background:#7c2d12;color:#fff;text-align:center;padding:8px;font-weight:700;font-size:13px}
.hero{background:linear-gradient(135deg,#fff7ed,#ffedd5);padding:30px 5%;text-align:center}
.hero h1{font-size:26px;color:#431407}
.cats{display:flex;gap:8px;padding:14px 4%;overflow-x:auto;white-space:nowrap;position:sticky;top:58px;background:rgba(255,250,247,0.98);z-index:90;border-bottom:1px solid #f0e6df}
.cat{padding:10px 18px;border-radius:30px;border:1.5px solid #fed7aa;background:#fff;font-weight:700;font-size:13px;cursor:pointer;flex-shrink:0}
.cat.active{background:#7c2d12;color:#fff;border-color:#7c2d12}
.products{display:grid;grid-template-columns:repeat(auto-fill,minmax(170px,1fr));gap:12px;padding:15px 4% 40px}
.card{background:#fff;border-radius:16px;overflow:hidden;box-shadow:0 4px 15px rgba(124,45,18,0.06);border:1px solid #fff1e6}
.card img{width:100%;height:150px;object-fit:cover;background:#fff7ed}
.card-body{padding:11px}
.card-body h3{font-size:13px;height:38px;overflow:hidden;color:#431407;font-weight:700}
.cat-label{font-size:11px;color:#c2410c;background:#fff7ed;border:1px solid #fed7aa;padding:2px 8px;border-radius:20px;display:inline-block;margin-bottom:5px}
.price{color:#ea580c;font-weight:800;font-size:15px;margin:6px 0}
.add-btn{width:100%;background:#fff7ed;border:1px solid #fed7aa;color:#7c2d12;padding:8px;border-radius:10px;font-weight:800;font-size:13px;cursor:pointer}
.page{display:none}
.page.active{display:block}
.pagination{display:flex;justify-content:center;gap:6px;padding:20px 0 30px}
.p-btn{width:38px;height:38px;border-radius:50%;border:1px solid #fed7aa;background:#fff;font-weight:800;cursor:pointer}
.p-btn.active{background:#7c2d12;color:#fff}
.cart-btn{position:relative;background:#7c2d12;color:#fff;border:none;padding:10px 20px;border-radius:30px;font-weight:800;cursor:pointer;font-size:13px}
#cart-count{position:absolute;top:-6px;left:-6px;background:#dc2626;color:#fff;width:19px;height:19px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:11px}
#cart-drawer{position:fixed;top:0;left:-100%;width:90%;max-width:380px;height:100%;background:#fff;z-index:300;box-shadow:15px 0 40px rgba(0,0,0,0.2);transition:0.3s;padding:20px;display:flex;flex-direction:column}
#cart-drawer.open{left:0}
.overlay{position:fixed;inset:0;background:rgba(0,0,0,0.4);display:none;z-index:250}
.overlay.show{display:block}
footer{background:#431407;color:#ffedd5;padding:30px 5%;text-align:center}
</style>
</head>
<body>
<div class="overlay" id="overlay" onclick="closeCart()"></div>
<header>
<div class="logo">فيصل <span>للسبوع والمناسبات</span></div>
<button class="cart-btn" onclick="openCart()">السلة <span id="cart-count">0</span></button>
</header>
<div class="shipping-bar">شحن داخل طنطا وجميع المحافظات - جملة وقطاعي - للتواصل واتساب 01120718712</div>
<section class="hero">
<h1>فيصل للسبوع والمناسبات</h1>
<p>كل مستلزمات السبوع واعياد الميلاد من مكان واحد - طنطا الغربية</p>
<p style="font-weight:800;color:#7c2d12;margin-top:8px">شحن داخل طنطا وجميع المحافظات</p>
</section>
<div class="cats">
<button class="cat active" onclick="showPage('all',this)">الكل</button>
<button class="cat" onclick="showPage('علب السبوع',this)">علب السبوع</button>
<button class="cat" onclick="showPage('ديكور',this)">ديكور</button>
<button class="cat" onclick="showPage('لعب اطفال',this)">لعب اطفال</button>
<button class="cat" onclick="showPage('شوكولاتة',this)">شوكولاتة</button>
<button class="cat" onclick="showPage('اعياد ميلاد',this)">لوازم اعياد الميلاد</button>
</div>
<div id="all" class="page active"><div class="products" id="products-all"></div><div class="pagination" id="pag-all"></div></div>
<div id="page-علب السبوع" class="page"><div class="products" id="products-علب السبوع"></div><div class="pagination" id="pag-علب السبوع"></div></div>
<div id="page-ديكور" class="page"><div class="products" id="products-ديكور"></div><div class="pagination" id="pag-ديكور"></div></div>
<div id="page-لعب اطفال" class="page"><div class="products" id="products-لعب اطفال"></div><div class="pagination" id="pag-لعب اطفال"></div></div>
<div id="page-شوكولاتة" class="page"><div class="products" id="products-شوكولاتة"></div><div class="pagination" id="pag-شوكولاتة"></div></div>
<div id="page-اعياد ميلاد" class="page"><div class="products" id="products-اعياد ميلاد"></div><div class="pagination" id="pag-اعياد ميلاد"></div></div>
<div id="cart-drawer"><h3 style="color:#7c2d12">سلة الطلبات</h3><div id="cart-items" style="flex:1;overflow:auto;margin-top:15px"></div><div style="border-top:2px dashed #fed7aa;padding-top:12px"><div style="display:flex;justify-content:space-between;font-weight:800;font-size:18px"><span>الاجمالي:</span><span id="total" style="color:#ea580c">0 جنيه</span></div><button onclick="checkout()" style="width:100%;background:#25D366;color:#fff;border:none;padding:13px;border-radius:12px;font-weight:800;margin-top:12px;cursor:pointer">اتمام الطلب واتساب</button><button onclick="closeCart()" style="width:100%;margin-top:8px;background:#fff7ed;border:1px solid #fed7aa;padding:9px;border-radius:10px;cursor:pointer">متابعة التسوق</button></div></div>
<footer><h3>فيصل للسبوع والمناسبات - طنطا</h3><p style="margin-top:8px">شحن داخل طنطا وجميع المحافظات</p><p>علب السبوع - ديكور - لعب اطفال - شوكولاتة - لوازم اعياد الميلاد</p><p style="margin-top:10px;font-weight:800">واتساب: 01120718712</p><p style="margin-top:6px;font-size:12px">طنطا - الغربية</p></footer>
<script>
const WHATSAPP="201120718712";
const ITEMS_PER_PAGE=8;
const products=[
{id:1,name:"علبة سبوع كرتون 50 قطعة الوان",price:300,cat:"علب السبوع",img:"https://images.unsplash.com/photo-1549007994-cb92caebd54b?w=400"},
{id:2,name:"علبة سبوع قطيفة فاخرة 30 قطعة",price:550,cat:"علب السبوع",img:"https://images.unsplash.com/photo-1606312619070-d48b4c652a52?w=400"},
{id:3,name:"علبة سبوع شفافة اكريليك",price:25,cat:"علب السبوع",img:"https://images.unsplash.com/photo-1515488042361-ee00e0ddd4e4?w=400"},
{id:4,name:"علبة سبوع خشب بالاسم",price:45,cat:"علب السبوع",img:"https://images.unsplash.com/photo-1549007994-cb92caebd54b?w=400"},
{id:5,name:"علبة سبوع معدن فضي",price:60,cat:"علب السبوع",img:"https://images.unsplash.com/photo-1515488042361-ee00e0ddd4e4?w=400"},
{id:6,name:"كروت سبوع وتوزيعات جاهزة",price:15,cat:"علب السبوع",img:"https://images.unsplash.com/photo-1515488042361-ee00e0ddd4e4?w=400"},
{id:7,name:"ديكور سبوع ولد ازرق وابيض كامل",price:450,cat:"ديكور",img:"https://images.unsplash.com/photo-1530103862676-de8c9debad1d?w=400"},
{id:8,name:"ديكور سبوع بنت روز جولد كامل",price:480,cat:"ديكور",img:"https://images.unsplash.com/photo-1522771930-78848d9293e8?w=400"},
{id:9,name:"ستارة اسم البيبي مع بلالين هيليوم",price:320,cat:"ديكور",img:"https://images.unsplash.com/photo-1522771930-78848d9293e8?w=400"},
{id:10,name:"طقم ديكور سبوع شامل بلالين وزينة",price:600,cat:"ديكور",img:"https://images.unsplash.com/photo-1530103862676-de8c9debad1d?w=400"},
{id:11,name:"زينة حائط سبوع Welcome Baby",price:150,cat:"ديكور",img:"https://images.unsplash.com/photo-1522771930-78848d9293e8?w=400"},
{id:12,name:"طقم لعب اطفال سبوع 7 قطع",price:120,cat:"لعب اطفال",img:"https://images.unsplash.com/photo-1596461404969-9ae70f2830c1?w=400"},
{id:13,name:"شخشيخة وعضاضة سيليكون للاطفال",price:65,cat:"لعب اطفال",img:"https://images.unsplash.com/photo-1551698618-1dfe5d97d256?w=400"},
{id:14,name:"ببرونة ولهاية طقم سبوع",price:95,cat:"لعب اطفال",img:"https://images.unsplash.com/photo-1551698618-1dfe5d97d256?w=400"},
{id:15,name:"لعبة دبدوب صغير للسبوع",price:40,cat:"لعب اطفال",img:"https://images.unsplash.com/photo-1596461404969-9ae70f2830c1?w=400"},
{id:16,name:"طقم رضع 3 قطع",price:110,cat:"لعب اطفال",img:"https://images.unsplash.com/photo-1551698618-1dfe5d97d256?w=400"},
{id:17,name:"شوكولاتة سبوع بالاسم 100 قطعة",price:400,cat:"شوكولاتة",img:"https://images.unsplash.com/photo-1549007994-cb92caebd54b?w=400"},
{id:18,name:"شوكولاتة محشية علبة فاخرة",price:180,cat:"شوكولاتة",img:"https://images.unsplash.com/photo-1549007994-cb92caebd54b?w=400"},
{id:19,name:"شوكولاتة سبوع مغلفة جاهزة",price:250,cat:"شوكولاتة",img:"https://images.unsplash.com/photo-1549007994-cb92caebd54b?w=400"},
{id:20,name:"طقم عيد ميلاد كامل 10 افراد",price:250,cat:"اعياد ميلاد",img:"https://images.unsplash.com/photo-1530103862676-de8c9debad1d?w=400"},
{id:21,name:"زينة عيد ميلاد Happy Birthday",price:120,cat:"اعياد ميلاد",img:"https://images.unsplash.com/photo-1530103862676-de8c9debad1d?w=400"},
{id:22,name:"شموع عيد ميلاد ارقام وتورتة",price:85,cat:"اعياد ميلاد",img:"https://images.unsplash.com/photo-1530103862676-de8c9debad1d?w=400"},
{id:23,name:"طربوش عيد ميلاد 6 قطع",price:60,cat:"اعياد ميلاد",img:"https://images.unsplash.com/photo-1530103862676-de8c9debad1d?w=400"},
{id:24,name:"بالونات هيليوم ارقام",price:90,cat:"اعياد ميلاد",img:"https://images.unsplash.com/photo-1530103862676-de8c9debad1d?w=400"},
];
let cart=[];let currentPages={};
function getFiltered(cat){if(cat==='all')return products;return products.filter(p=>p.cat===cat);}
function renderPage(cat,pageNum=1){
const list=getFiltered(cat);const totalPages=Math.ceil(list.length/ITEMS_PER_PAGE);currentPages[cat]=pageNum;const start=(pageNum-1)*ITEMS_PER_PAGE;const slice=list.slice(start,start+ITEMS_PER_PAGE);const containerId=cat==='all'?'products-all':'products-'+cat;document.getElementById(containerId).innerHTML=slice.map(p=>`<div class="card"><img src="${p.img}" loading="lazy"><div class="card-body"><span class="cat-label">${p.cat}</span><h3>${p.name}</h3><div class="price">${p.price} جنيه</div><button class="add-btn" onclick="addToCart(${p.id})">اضف للسلة</button></div></div>`).join('');const pagId=cat==='all'?'pag-all':'pag-'+cat;let pagHtml='';for(let i=1;i<=totalPages;i++){pagHtml+=`<button class="p-btn ${i===pageNum?'active':''}" onclick="renderPage('${cat}',${i})">${i}</button>`;}document.getElementById(pagId).innerHTML=pagHtml;
}
['all','علب السبوع','ديكور','لعب اطفال','شوكولاتة','اعياد ميلاد'].forEach(c=>renderPage(c,1));
function showPage(cat,el){document.querySelectorAll('.cat').forEach(x=>x.classList.remove('active'));el.classList.add('active');document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));if(cat==='all'){document.getElementById('all').classList.add('active');}else{document.getElementById('page-'+cat).classList.add('active');}window.scrollTo({top:280,behavior:'smooth'});}
function addToCart(id){let p=products.find(x=>x.id===id);let ex=cart.find(x=>x.id===id);if(ex)ex.qty++;else cart.push({...p,qty:1});updateCart();openCart();}
function updateCart(){document.getElementById('cart-count').innerText=cart.reduce((s,i)=>s+i.qty,0);let d=document.getElementById('cart-items');if(!cart.length){d.innerHTML="<p style='text-align:center;color:#888;margin-top:30px'>السلة فارغة</p>";}else{d.innerHTML=cart.map(i=>`<div style='display:flex;gap:10px;margin-bottom:12px;border-bottom:1px solid #ffedd5;padding-bottom:10px'><img src='${i.img}' style='width:55px;height:55px;border-radius:10px;object-fit:cover'><div style='flex:1'><div style='font-size:12px;font-weight:700'>${i.name}</div><div style='color:#ea580c;font-weight:800'>${i.price}ج x ${i.qty} = ${i.price*i.qty}ج</div><button onclick='removeItem(${i.id})' style='color:#dc2626;background:none;border:none;font-size:11px;cursor:pointer'>حذف</button></div></div>`).join('');}document.getElementById('total').innerText=cart.reduce((s,i)=>s+i.price*i.qty,0)+" جنيه";}
function removeItem(id){cart=cart.filter(i=>i.id!==id);updateCart();}
function openCart(){document.getElementById('cart-drawer').classList.add('open');document.getElementById('overlay').classList.add('show');}
function closeCart(){document.getElementById('cart-drawer').classList.remove('open');document.getElementById('overlay').classList.remove('show');}
function checkout(){if(!cart.length){alert('السلة فارغة');return;}let msg="السلام عليكم فيصل للسبوع والمناسبات%0Aعايز اطلب:%0A%0A";cart.forEach(i=>{msg+=`- ${i.name} (${i.qty}) = ${i.price*i.qty}ج%0A`;});msg+=`%0Aالاجمالي: ${cart.reduce((s,i)=>s+i.price*i.qty,0)} جنيه%0A%0Aشحن داخل طنطا وجميع المحافظات`;window.open(`https://wa.me/${WHATSAPP}?text=${msg}`,"_blank");}
</script>
</body>
</html>
