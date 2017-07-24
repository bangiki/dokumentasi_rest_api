# Dokumentasi API Endpoint

## SIMAS ADI SANGGORO (Sistem Informasi Manajemen Aset Adi Sanggoro) 

SIMAS merupakan sistem informasi manajemen aset di SMK Adi Sanggoro, guna mengatur peminjaman,  pengembalian, dan pengecekan barang.

Jika ingin melihat repositori yang sedang dikembangkan cek [disini](https://github.com/ramdanix/dokumentasi_rest_api/blob/master/REPOSITORIES.md)

## Feature

- Pengecekan Barang
- Peminjaman Barang
- Pengembalian Barang
- Chart Barang Yang Sering Dipinjam

## EndPoint

Berikut list Endpoint API per-feature

- [Register User](https://github.com/ramdanix/dokumentasi_rest_api/blob/master/README.md#register-user)
- [Auth User](https://github.com/ramdanix/dokumentasi_rest_api/blob/master/README.md#auth-user)
- [Pengecekan Barang]()
- [Pengecekan Siswa]()
- [Peminjaman Barang]()
- [Pengembalian Barang]()

## Authentikasi

## POST  
### Register User

URL Request

``` bash
//local
http://apisimanset.dev/api/v1/auth/register

//production
http://apisimanset.trycatch.id/api/v1/auth/register
```

Header

Field | Value | 
------------ | ------------- 
**Content-Type** | application/json 
**Accept** | application/json 

Body

Field | Type Data | Validation
------------ | ------------- | -------------
**name** | String | required
**email** | String | required email
**password** | String | required min:6
**level** | 1 | required


Response

``` json
{
	"data": {
		"id": 5,
		"name": "rizki",
		"email": "ramdani3@gmail.com",
		"level": 0,
		"registered": "1 second ago"
	}
}
```

### Auth User

URL Request

``` bash
//local
http://apisimanset.dev/api/v1/auth/login

//production
http://apisimanset.trycatch.id/api/v1/auth/login
```

Header

Field | Value | 
------------ | ------------- 
**Content-Type** | application/json 
**Accept** | application/json 

Body

Field | Type Data | Validation
------------ | ------------- | -------------
**email** | String | required email
**password** | String | required min:6

Response

``` json
{
	"data": {
		"id": 3,
		"name": "rizki",
		"email": "ramdani@gmail.com",
		"level": 0,
		"registered": "55 minutes ago",
		"pinjams": {
			"data": []
		}
	},
	"meta": {
		"token": "Ym53aVdTVXpsY2Z0dkk0dGJQNjVIOGgzUUo5cE1mTnR3UFo5Yk5UeA=="
	}
}
```

## Pengecekan Barang

Barang yang dicek merupakan barang yang berada didalam ruangan kelas seperti meja, kursi, dll. 

## GET

Request

``` bash
http://apisimanset.dev/api/v1/inv-barang/detail/{id_inv_barang}
```

Header

**none**

Body

**none**

Parameter

Param | Type Data | 
------------ | ------------- 
**id_inv_barang** | String 

Response

``` json
{
    "data": {
        "petugas": "septian",
        "detail": {
            "inv_ruang_id": "INVB0012",
            "nama_barang": "Leptop Acer",
            "foto": "INVB0013.jpg",
            "label_barang": "116\/III\/LAP.smk\/R.KTR\/2012",
            "lokasi": "Ruang Kelas X TI 2",
            "kondisi": "Rusak",
            "tahun": 2015,
            "tanggal_input": "20 jam yang lalu"
        }
    }
}
```

## GET

Request

``` bash
http://apisimanset.dev/api/v1/inv-barang-ruang/detail/{id_inv_ruang}
```

Header

**none**

Body

**none**

Parameter

Param | Type Data | 
------------ | ------------- 
**id_inv_ruang** | String 

Example

``` bash
http://apisimanset.trycatch.id/api/v1/inv-barang-ruang/detail/INVR0002
```


Response

``` json
{
    "data": {
        "petugas": "septian",
        "detail": {
            "inv_ruang_id": "INVR0002",
            "nama_barang": "Meja Kayu & Besi",
            "foto": "INVR0003.jpg",
            "label_barang": "111\/III\/LAP.smk\/R.KTR\/2012",
            "jenis": "Kelengkapan",
            "lokasi": "Ruang Kelas X TI 2",
            "kondisi": "Rusak",
            "tahun": "2015",
            "tanggal_input": "4 bulan yang lalu"
        }
    }
}
```

### POST

## Peminjaman Barang

Barang yang dipinjam merupakan barang yang berada didalam kantor seperti infokus, terminal, leptop, bola, dll. 

## List All Peminjaman
## GET

Request

``` bash
http://apisimanset.trycatch.id/api/v1/peminjaman/all/{id_petugas}
```

Header

**none**

Body

**none**

Parameter

Param | Type Data | 
------------ | ------------- 
**id_petugas** | Integer 

Response

``` json
{
    "data": [
        {
            "uuid_pinjam": "33c8660e-1e97-11e7-9155-75a5a6462ab5",
            "nis": 85892740,
            "nama": "Ismi Widiastuti",
            "kelas": "XI RPL 3",
            "date_pinjam": "2017-04-11 16:14:01",
            "waktu_pinjam": "3 bulan yang lalu",
            "petugas": 1,
            "keterangan": "saya pinjam barang"
        },
        {
            "uuid_pinjam": "f33c69ae-0fd8-11e7-ba84-f45565668763",
            "nis": 85892740,
            "nama": "Ismi Widiastuti",
            "kelas": "XI RPL 3",
            "date_pinjam": "2017-03-23 21:56:52",
            "waktu_pinjam": "3 bulan yang lalu",
            "petugas": 1,
            "keterangan": "barang telah kembali"
        }
    ]        
}
```
## Get Item Peminjaman
## GET

Request

``` bash
http://apisimanset.trycatch.id/api/v1/peminjaman/item/{uuid}
```

Header

**none**

Body

**none**

Parameter

Param | Type Data | 
------------ | ------------- 
**uuid** | String 

Example
``` bash
http://apisimanset.trycatch.id/api/v1/peminjaman/item/91e9ae2c-67d6-11e7-af48-277366abe596
```

Response

``` json
{
    "data": [
        {
            "kode_barang": "INVB0010",
            "nama_barang": "Sound System Span",
            "label_barang": "115\/III\/LAP.smk\/R.KTR\/2012",
            "lokasi_barang": "-",
            "kondisi_barang": "Baik"
        }
    ]
}
```

## Store Peminjaman
## POST

Request

``` bash
http://apisimanset.trycatch.id/api/v1/peminjaman/save
```

Header

Field | Value | 
------------ | ------------- 
**Content-Type** | application/json 
**Accept** | application/json 

Body

Field | Type Data | Validation
------------ | ------------- | -------------
**nis** | String | -
**petugas** | String | -
**uuid** | String | -
**waktu_pinjam** | String | -
**barang** | Array | -

Format JSON Body

``` json
{
    "barang":[
        {
            "date":"Jul 13, 2017 9:08:14 PM",
            "id":1,
            "kode_barang":"INVB0010",
            "kondisi_barang":"Baik",
            "label_barang":"115/III/LAP.smk/R.KTR/2012",
            "lokasi_barang":"-",
            "nama_barang":"Sound System Span",
            "type":"TEXT"
        },
        {
            "date":"Jul 13, 2017 9:08:14 PM",
            "id":1,
            "kode_barang":"INVB0002",
            "kondisi_barang":"Baik",
            "label_barang":"115/III/LAP.smk/R.KTR/2012",
            "lokasi_barang":"-",
            "nama_barang":"Sound System Span",
            "type":"TEXT"
        }
        ],
    "nama":"Astria Handayani",
    "nis":10150159,
    "petugas":1,
    "uuid":0,
    "waktu_pinjam":"3 bulan yang lalu"
}
```


Response

``` json
{
	"pesan": "sukses",
	"error": false
}
```

## Pengembalian Barang

## GET

Request

``` bash
http://apisimanset.trycatch.id/api/v1/peminjaman/all/{id_petugas}
```

Header

**none**

Body

**none**

Parameter

Param | Type Data | 
------------ | ------------- 
**id_petugas** | Integer 

Response

``` json
{
    "data": [
        {
            "uuid_pinjam": "33c8660e-1e97-11e7-9155-75a5a6462ab5",
            "nis": 85892740,
            "nama": "Ismi Widiastuti",
            "kelas": "XI RPL 3",
            "date_pinjam": "2017-04-11 16:14:01",
            "waktu_pinjam": "3 bulan yang lalu",
            "petugas": 1,
            "keterangan": "saya pinjam barang"
        },
        {
            "uuid_pinjam": "f33c69ae-0fd8-11e7-ba84-f45565668763",
            "nis": 85892740,
            "nama": "Ismi Widiastuti",
            "kelas": "XI RPL 3",
            "date_pinjam": "2017-03-23 21:56:52",
            "waktu_pinjam": "3 bulan yang lalu",
            "petugas": 1,
            "keterangan": "barang telah kembali"
        }
    ]        
}
```

## Chart Peminjaman Barang

### GET

Request

Response

## Siswa

Aktor peminjam barang

## Detail Siswa

menampilkan detail siswa berdasarkan nis

## GET

Request

``` bash
http://apisimanset.trycatch.id/api/v1/siswa/detail/{nis}
```

Header

**none**

Body

**none**

Parameter

Param | Type Data | 
------------ | ------------- 
**nis** | Integer 

Response

``` json
{
    "data": {
        "nis": 10150171,
        "nama": "Dinda Ayu Syafitri",
        "kelas": "XI RPL 3",
        "jurusan": "Rekayasa Perangkat Lunak",
        "semester": 1,
        "photo": "",
        "status": "aktif",
        "created_at": "3 bulan yang lalu"
    }
}
```
``` json
{
    "data": {
        "nis": 10150171,
        "nama": "Dinda Ayu Syafitri",
        "kelas": "XI RPL 3",
        "jurusan": "Rekayasa Perangkat Lunak",
        "semester": 1,
        "photo": "",
        "status": "aktif",
        "created_at": "3 bulan yang lalu"
    }
}
```

## Store Pengembalian
## POST

Request

``` bash
http://apisimanset.trycatch.id/api/v1/pengembalian/save
```

Header

Field | Value | 
------------ | ------------- 
**Content-Type** | application/json 
**Accept** | application/json 

Body

Field | Type Data | Validation
------------ | ------------- | -------------
**nis** | String | -
**petugas** | String | -
**uuid_pinjam** | String | -
**barang** | Array | -

Format Body

``` json
{
    "barang":[
        {
            "kode_barang":"INVB0010",
            "kondisi_barang":"Baik",
            "label_barang":"115/III/LAP.smk/R.KTR/2012",
            "lokasi_barang":"-",
            "nama_barang":"Sound System Span"
        },
        {
            "kode_barang":"INVB0002",
            "kondisi_barang":"Baik",
            "label_barang":"111/III/LAP.smk/R.KTR/2012",
            "lokasi_barang":"Ruang Kelas X TI 1",
            "nama_barang":"Sound System Toshiba"
        }
    ],
    "nis":10150159,
    "petugas":1,
    "uuid_pinjam":"bab81d8e-67d6-11e7-89eb-2c1f3ddcc75b"
}

```

Response
``` json
{
    "pesan": "data berhasil dikembalikan",
    "error": false
}
```