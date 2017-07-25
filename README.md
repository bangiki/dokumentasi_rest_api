# Dokumentasi API SIMANSET

## SIMAS ADI SANGGORO (Sistem Informasi Manajemen Aset Adi Sanggoro) 

SIMAS merupakan sistem informasi manajemen aset di SMK Adi Sanggoro, guna mengatur peminjaman,  pengembalian, dan pengecekan barang.

Jika ingin melihat repositori yang sedang dikembangkan cek [disini](https://github.com/ramdanix/dokumentasi_rest_api/blob/master/REPOSITORIES.md)

## Feature

- Pengecekan Barang
- Peminjaman Barang
- Pengembalian Barang
- Chart Barang Yang Sering Dipinjam

## URL EndPoint

Berikut list URL Endpoint API per-feature

- [Register User](https://github.com/ramdanix/dokumentasi_rest_api/blob/master/README.md#register-user)
- [Auth User](https://github.com/ramdanix/dokumentasi_rest_api/blob/master/README.md#auth-user)
- [Pengecekan Barang](https://github.com/ramdanix/dokumentasi_rest_api/blob/master/README.md#pengecekan-barang)
- [Peminjaman Barang](https://github.com/ramdanix/dokumentasi_rest_api/blob/master/README.md#peminjaman-barang)
- [Pengembalian Barang](https://github.com/ramdanix/dokumentasi_rest_api/blob/master/README.md#pengembalian-barang)
- [Report Barang Pinjam (Chart)](https://github.com/ramdanix/dokumentasi_rest_api/blob/master/README.md#pengembalian-barang)

## Authentikasi

## POST  
### Register User

URL Request

**Production**
``` bash
http://apisimanset.dev/api/v1/auth/register
```

**Production**

``` bash
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


**Local**

``` bash
http://apisimanset.dev/api/v1/auth/login
```

**Production**

``` bash
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

``` jsonPelajar -> Lihat API
Scan Barang ya
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

Barang yang dicek merupakan barang yang berada didalam ruangan kelas seperti meja, kursi, dan lain-lain. 

Pengecekan Barang dibagi 2 yaitu 
- [Pengecekan Barang Inventaris](https://github.com/ramdanix/dokumentasi_rest_api/blob/master/README.md#pengecekan-barang-inventaris)
- [Pengecekan Barang Pada Ruang](https://github.com/ramdanix/dokumentasi_rest_api/blob/master/README.md#pengecekan-barang-pada-ruang)

## Pengecekan Barang Inventaris

## GET

URL Request

**Local**
``` bash
http://apisimanset.dev/api/v1/inv-barang/detail/{id_inv_barang}
```

**Production**
``` bash
http://apisimanset.trycatch.id/api/v1/inv-barang/detail/{id_inv_barang}
```

Header

Field | Value | 
------------ | ------------- 
**Authorization** | String token 

Bulk Header

``` bash
Authorization: Bearer SFM3bE90NWF6NUlLRGk5aUR4czZtUTVwM0dHd1V0RzRpRHBFMTRYdw==
```

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

## Pengecekan Barang Pada Ruang

## GET

URL Request

**Local**
``` bash
http://apisimanset.dev/api/v1/inv-barang-ruang/detail/{id_inv_ruang}
```

**Production**
``` bash
http://apisimanset.trycatch.id/api/v1/inv-barang-ruang/detail/{id_inv_ruang}
```

Header

Field | Value | 
------------ | ------------- 
**Authorization** | String token 

Bulk Header

``` bash
Authorization: Bearer SFM3bE90NWF6NUlLRGk5aUR4czZtUTVwM0dHd1V0RzRpRHBFMTRYdw==
```

Body

**none**

Parameter

Param | Type Data | 
------------ | ------------- 
**id_inv_ruang** | String 

Response

``` json
{
    "data": {
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

## Peminjaman Barang

Peminjaman dilakukan dengan 3 Tahap

1. Scan Kartu Pelajar -> [LihatAPI](https://github.com/ramdanix/dokumentasi_rest_api/blob/master/README.md#siswa)
2. Scan Barang yang akan dipinjam -> [Lihat API](https://github.com/ramdanix/dokumentasi_rest_api/blob/master/README.md#pengecekan-barang-inventaris)
3. Store data siswa dan data barang yang akan dipinjam -> [Lihat API](https://github.com/ramdanix/dokumentasi_rest_api/blob/master/README.md#store-data-user--barang-pinjam)
4. Lihat data semua peminjaman -> [Lihat API](https://github.com/ramdanix/dokumentasi_rest_api/blob/master/README.md#list-all-peminjaman)
5. Lihat item pinjam berdasarkan user -> [Lihat API](https://github.com/ramdanix/dokumentasi_rest_api/blob/master/README.md#get-list-item-peminjaman)

## Siswa

Aktor peminjam barang, petugas menyecan kartu pelajar yang dimiliki siswa

## Detail Siswa

menampilkan detail siswa berdasarkan nis yang tertera pada kartu pelajar.

## GET

URL Request


**Local**
``` bash
http://apisimanset.dev/api/v1/siswa/detail/{nis}
```

**Production**
``` bash
http://apisimanset.trycatch.id/api/v1/siswa/detail/{nis}
```

Header

Field | Value | 
------------ | ------------- 
**Authorization** | String token 

Bulk Header

``` bash
Authorization: Bearer SFM3bE90NWF6NUlLRGk5aUR4czZtUTVwM0dHd1V0RzRpRHBFMTRYdw==
```

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

## Store Data User & Barang Pinjam

Menyimpan data user dan data barang yang dipinjam.

## POST

URL Request

**Local**

``` bash
http://apisimanset.dev/api/v1/peminjaman/save
```

**Production**

``` bash
http://apisimanset.trycatch.id/api/v1/peminjaman/save
```

Header

Field | Value | 
------------ | ------------- 
**Content-Type** | application/json 
**Accept** | application/json
**Authorization** | String token 

Bulk Header

``` bash
Authorization: Bearer SFM3bE90NWF6NUlLRGk5aUR4czZtUTVwM0dHd1V0RzRpRHBFMTRYdw==
```

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


## List All Peminjaman

menampilkan seluruh data peminjaman

## GET

URL Request

**Local**
``` bash
http://apisimanset.dev/api/v1/peminjaman/history/all/{id_petugas}
```

**Production**

``` bash
http://apisimanset.trycatch.id/api/v1/peminjaman/history/all/{id_petugas}
```

Header

Field | Value | 
------------ | ------------- 
**Authorization** | String token 

Bulk Header

``` bash
Authorization: Bearer SFM3bE90NWF6NUlLRGk5aUR4czZtUTVwM0dHd1V0RzRpRHBFMTRYdw==
```



> **Untuk akses web tidak perlu memakai token URL menjadi**



**Local**
``` bash
http://apisimanset.dev/api/v1/peminjaman/history/all/no-token/{id_petugas}
```

**Production**

``` bash
http://apisimanset.trycatch.id/api/v1/peminjaman/history/all/no-token/{id_petugas}
```

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

## Get List Item Peminjaman

## GET

URL Request

**Local**
``` bash
http://apisimanset.dev/api/v1/peminjaman/item/{uuid}
```

**Production**

``` bash
http://apisimanset.trycatch.id/api/v1/peminjaman/item/{uuid}
```

Header

Field | Value | 
------------ | ------------- 
**Authorization** | String token 

Bulk Header

``` bash
Authorization: Bearer SFM3bE90NWF6NUlLRGk5aUR4czZtUTVwM0dHd1V0RzRpRHBFMTRYdw==
```

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


## Pengembalian Barang

## GET

URL Request

**Local**

``` bash
http://apisimanset.dev/api/v1/pengembalian/history/all/{id_petugas}
```

**Production**

``` bash
http://apisimanset.trycatch.id/api/v1/pengembalian/history/all/{id_petugas}
```

Header

Field | Value | 
------------ | ------------- 
**Authorization** | String token 

Bulk Header

``` bash
Authorization: Bearer SFM3bE90NWF6NUlLRGk5aUR4czZtUTVwM0dHd1V0RzRpRHBFMTRYdw==
```

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

## Store Pengembalian Barang

## POST

URL Request

**Local**

``` bash
http://apisimanset.dev/api/v1/pengembalian/save
```

**Production**

``` bash
http://apisimanset.trycatch.id/api/v1/pengembalian/save
```

Header

Field | Value | 
------------ | ------------- 
**Content-Type** | application/json 
**Accept** | application/json
**Authorization** | String token 

Bulk Header

``` bash
Authorization: Bearer SFM3bE90NWF6NUlLRGk5aUR4czZtUTVwM0dHd1V0RzRpRHBFMTRYdw==
```

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


## Report Peminjaman Barang

API ini berfungsi untuk menampilkan 4 data barang yang sering dipinjam dan akan ditampilkan berupa chart.

### GET

URL Request

**Local**

``` bash
http://apisimanset.dev/api/v1/peminjaman/report/chart/{id_petugas}
```

**Production**

``` bash
http://apisimanset.trycatch.id/api/v1/peminjaman/report/chart/{id_petugas}
```

Header

Field | Value | 
------------ | ------------- 
**Authorization** | String token 

Bulk Header

``` bash
Authorization: Bearer SFM3bE90NWF6NUlLRGk5aUR4czZtUTVwM0dHd1V0RzRpRHBFMTRYdw==
```

Parameter

Param | Type Data | 
------------ | ------------- 
**id_petugas** | Integer 


Response

``` json
{
	"INVB0000": 1,
	"INVB0002": 2,
	"INVB0004": 3,
	"INVB0006": 2
}
```


