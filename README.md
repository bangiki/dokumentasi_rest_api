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

### List All Peminjaman

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
        },
        ......
}
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