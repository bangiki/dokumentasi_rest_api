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

## Authentikasi

## GET

**Request**

**Response**

## POST  
### Register User

Request

``` bash
http://simanset.dev/api/v1/auth/register
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

Response

``` json
{
    "data": {
        "name": "rizki",
        "email": "ramdani.rizki19@gmail.com",
        "registered": "1 detik yang lalu"
    },
    "meta": {
        "token": "$2y$10$l7\/CT7Plk2rI9bpWC\/wDHuwYUjI3Vd5wykCVsaJW3YbSj\/k46u01G"
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

### POST

## Peminjaman Barang

Barang yang dipinjam merupakan barang yang berada didalam kantor seperti infokus, terminal, leptop, bola, dll. 

## GET

### List All Peminjaman

Request

``` bash
http://apisimanset.dev/api/v1/peminjaman/all
```

Parameter

First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column

Response

``` json
http://apisimanset.dev/api/v1/peminjaman/all
```

### POST

Request

Response

## Pengembalian Barang

### GET

Request

Response

### POST

Request

Response

## Chart Peminjaman Barang

### GET

Request

Response