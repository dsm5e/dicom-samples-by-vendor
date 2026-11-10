# dicom-samples-by-vendor

A source-linked index of public DICOM sample studies, research datasets, decoder fixtures and NIfTI examples, grouped by modality and scanner or software vendor. Intended for viewer development, import checks and reproducible testing.

This repository contains **links and descriptions only**. It does not host, copy or redistribute image files, patient records or vendor installers. Each listed download remains with its publisher or the maintainer of the particular derived test fixture.

Last source check: **2026-11-10**. **17 entries:** 2 dental CBCT, 3 CT, 6 MRI, 4 transfer-syntax fixture selections and 2 NIfTI examples. Multi-vendor collections count once. Enhanced multi-frame references reuse MRI entries.

## How to use

1. Choose a modality, vendor or [format test](#transfer-syntax-and-enhanced-multi-frame-tests).
2. Open the original source, review its current terms and choose the specific study, subset or filenames listed here.
3. Obtain permitted files directly from that source. Keep series folders together; extract ZIP archives and, where necessary, decompress individual `.dcm.gz` files before importing.
4. Use [datasets.json](datasets.json) for filtering and source evidence. It records registration uncertainty, exact byte counts where available, verification methods and candidates excluded from the tables.

“Source-verified” means a web search was performed and the source page or its repository metadata was opened. It does **not** mean a binary download, pixel/header audit, working-download test or viewer compatibility test was performed. No image files were fetched during this check. Known patient-identifiable data and private clinic exports are outside scope.

Vendor/model and transfer syntax are reported only where a source supports them. **Not stated** is not a guess. **“terms not stated” does not grant reuse permission.** A repository's software licence does not automatically settle upstream image rights.

Sizes retain the publisher's units. GitHub sizes are sums of stored file sizes from a recorded tree, excluding listed documentation sidecars; they are not ZIP download sizes or decompressed sizes. The Philips CT subtree total includes directory records. Full scope and tree hashes are in the JSON.

## Dental CBCT

| Source / vendor and model | Contents | Transfer syntax | Size | Source licence or terms | Registration / access |
| --- | --- | --- | --- | --- | --- |
| <a id="dental-missing-teeth"></a>[Adult dental CBCT: missing teeth, version 2](https://www.scidb.cn/detail?dataSetId=7524d88b52574de28477eb341eb33ee4)<br>NewTom: VGi; KaVo: OP 3D Vision V17; Meyer: SS-X9010DPro | 158 CBCT volumes (59,978 slices), with JSON annotations for 85 subjects; DICOM data arranged by scanner. | not stated | 23,534,221,851 bytes (repaired ZIP) | ["Creative Commons Attribution 4.0 International (CC-BY 4.0)"](https://www.nature.com/articles/s41597-026-07156-9) | **Unknown.** Download registration not confirmed. Repository metadata says PUBLIC; landing page is accessible without login. |
| <a id="dental-physionet"></a>[Multimodal dental dataset, version 1.1.0](https://physionet.org/content/multimodal-dental-dataset/1.1.0/)<br>not stated | 329 CBCT volumes from 169 patients, 8 panoramic DICOM images and 16,203 synthetic periapical TIFF images. | not stated | not stated | ["PhysioNet Contributor Review Health Data License 1.5.0"](https://physionet.org/content/multimodal-dental-dataset/view-license/1.1.0/) | **Yes.** Credentialed account, required training, signed data use agreement and contributor approval of the proposed study. |

The ScienceDB vendor/model and de-identification evidence comes from its [dataset paper](https://www.nature.com/articles/s41597-026-07156-9). Use version 2's repaired archive. Public access metadata does not settle whether an account is needed to download.

PhysioNet is a **restricted research resource**, with credentialing and study approval. Its [licence](https://physionet.org/content/multimodal-dental-dataset/view-license/1.1.0/) limits use to lawful scientific research and prohibits sharing access to the restricted data.

### Requested dental vendor coverage

A gap means this pass did not verify a suitable public source; it does not mean none exists. Unverified candidates below are not included as datasets.

| Vendor / ecosystem | Verified entry | Coverage |
| --- | --- | --- |
| Planmeca | — | Only out-of-scope knee projection data verified. |
| Carestream | — | Demo candidates lack sufficient sample-specific evidence. |
| Sirona / Sidexis / Galileos | — | No suitable source verified. Sidexis is software; no scanner is inferred from it. |
| Vatech | — | No suitable public DICOM source verified. |
| NewTom | [Adult dental CBCT: missing teeth, version 2](#dental-missing-teeth) | VGi stated in the dataset paper. |
| i-CAT / KaVo | [Adult dental CBCT: missing teeth, version 2](#dental-missing-teeth) | KaVo OP 3D Vision V17 verified; i-CAT-branded data not established. |
| Morita | — | Viewer demo candidate remains unverified. |
| Anatomage | — | Software vendor; no suitable standalone public DICOM source verified. |

## CT

| Source / vendor and model | Contents | Transfer syntax | Size | Source licence or terms | Registration / access |
| --- | --- | --- | --- | --- | --- |
| <a id="ct-credence-phantom"></a>[Credence Cartridge Radiomics Phantom](https://www.cancerimagingarchive.net/collection/cc-radiomics-phantom/)<br>GE: model not stated; Philips: model not stated; Siemens: model not stated; Toshiba: model not stated | 17 phantom scans: GE 7, Philips 5, Siemens 2, Toshiba 3; 51 series and 2,672 images, including CT and RTSTRUCT. | not stated | 1.43 GB | ["CC BY 3.0"](https://www.cancerimagingarchive.net/collection/cc-radiomics-phantom/) | **No.** Public collection; TCIA Data Retriever is needed for the manifest workflow. No account indicated for public access. |
| <a id="ct-philips-gantry"></a>[dcm_qa_ct](https://github.com/neurolabusc/dcm_qa_ct)<br>Philips: Ingenuity | Phantom CT with varying gantry tilt; index scope is In/Philips/ only. | not stated | 232,950,916 bytes (445 stored files; manifest total); Philips subtree only | ["BSD 2-Clause License"](https://github.com/neurolabusc/dcm_qa_ct/blob/master/LICENSE) (repository) | **No.** Public GitHub files; no registration needed. |
| <a id="synthetic-ct"></a>[CT-01 synthetic chest](https://www.charruasoft.com/dicom-samples/)<br>CharruaSoft (software; synthetic data) | 40 axial slices of a mathematical torso phantom, 512 × 512. | Explicit VR Little Endian (`1.2.840.10008.1.2.1`) | 20.1 MB | ["CC0 1.0"](https://www.charruasoft.com/dicom-samples/) | **No.** Public sample download links; no account requested. |

The TCIA collection is a physical phantom, with a required [collection citation and usage policy](https://www.cancerimagingarchive.net/collection/cc-radiomics-phantom/). Its Toshiba-labelled scans are recorded as Toshiba; the index does not relabel them as a Canon scanner model. For `dcm_qa_ct`, only the **Philips phantom subtree** is included.

## MRI

| Source / vendor and model | Contents | Transfer syntax | Size | Source licence or terms | Registration / access |
| --- | --- | --- | --- | --- | --- |
| <a id="mri-siemens-xa30"></a>[dcm_qa_xa30](https://github.com/neurolabusc/dcm_qa_xa30)<br>Siemens: Prisma Fit | MR XA30 enhanced DICOM: structural, functional, diffusion, ASL and field-map tests. | not stated | 66,924,708 bytes (95 stored files; manifest total) | ["BSD 2-Clause License"](https://github.com/neurolabusc/dcm_qa_xa30/blob/main/LICENSE) (repository); ["CC BY 4.0"](https://www.nature.com/articles/s41597-025-05503-w) (image reuse) | **No.** Public GitHub files; no registration needed. |
| <a id="mri-ge"></a>[dcm_qa_ge](https://github.com/neurolabusc/dcm_qa_ge)<br>GE: SIGNA Pioneer, SIGNA Architect | Diffusion MRI and functional MRI conversion tests, including acceleration and slice timing. | not stated | 148,990,852 bytes (4,360 stored files; manifest total) | ["BSD 2-Clause License"](https://github.com/neurolabusc/dcm_qa_ge/blob/master/LICENSE) (repository); ["CC BY 4.0"](https://www.nature.com/articles/s41597-025-05503-w) (image reuse) | **No.** Public GitHub files; no registration needed. |
| <a id="mri-philips-enhanced"></a>[dcm_qa_philips_enh](https://github.com/neurolabusc/dcm_qa_philips_enh)<br>Philips: Ingenia Elition X | Matching classic and enhanced MRI exports: structural, ASL, field maps, functional MRI and diffusion. | not stated | 151,462,108 bytes (7,370 stored files; manifest total) | ["BSD 2-Clause License"](https://github.com/neurolabusc/dcm_qa_philips_enh/blob/main/LICENSE) (repository); ["CC BY 4.0"](https://www.nature.com/articles/s41597-025-05503-w) (image reuse) | **No.** Public GitHub files; no registration needed. |
| <a id="mri-canon"></a>[dcm_qa_canon](https://github.com/neurolabusc/dcm_qa_canon)<br>Canon: Galan3T | Classic MRI diffusion-direction and angulation tests; software V6.0SP2000. | not stated | 89,375,242 bytes (5,720 stored files; manifest total) | ["BSD 2-Clause License"](https://github.com/neurolabusc/dcm_qa_canon/blob/master/LICENSE) (repository); ["CC BY 4.0"](https://www.nature.com/articles/s41597-025-05503-w) (image reuse) | **No.** Public GitHub files; no registration needed. |
| <a id="mri-united-imaging"></a>[dcm_qa_uih](https://github.com/neurolabusc/dcm_qa_uih)<br>United Imaging Healthcare: model not stated | Structural and diffusion MRI conversion tests; scanner model not stated. | not stated | 169,352,118 bytes (388 stored files; manifest total) | ["BSD 2-Clause License"](https://github.com/neurolabusc/dcm_qa_uih/blob/master/LICENSE) (repository); ["CC BY 4.0"](https://www.nature.com/articles/s41597-025-05503-w) (image reuse) | **No.** Public GitHub files; no registration needed. |
| <a id="synthetic-mr"></a>[MR-01 synthetic brain](https://www.charruasoft.com/dicom-samples/)<br>CharruaSoft (software; synthetic data) | Two 20-slice T1/T2 phantom series, 256 × 256. | Explicit VR Little Endian (`1.2.840.10008.1.2.1`) | 5.1 MB | ["CC0 1.0"](https://www.charruasoft.com/dicom-samples/) | **No.** Public sample download links; no account requested. |

The [dcm_qa collection paper](https://www.nature.com/articles/s41597-025-05503-w) describes phantom acquisitions and human scans from volunteers aware of public release. It reports varying de-identification practices and an image-reuse option under CC BY 4.0. These publisher statements are not an independent privacy audit. Original DICOM inputs are in `In/`; `Ref/` holds conversion references.

The [Canon README](https://github.com/neurolabusc/dcm_qa_canon/blob/master/README.MD) documents a diffusion-gradient orientation limitation. Philips `.dcm.gz` denotes external gzip wrapping, not a DICOM compression syntax.

### CT/MRI vendor lookup

| Vendor | Entries |
| --- | --- |
| Siemens | [Credence Cartridge Radiomics Phantom](#ct-credence-phantom); [dcm_qa_xa30](#mri-siemens-xa30) |
| GE | [Credence Cartridge Radiomics Phantom](#ct-credence-phantom); [dcm_qa_ge](#mri-ge) |
| Philips | [Credence Cartridge Radiomics Phantom](#ct-credence-phantom); [dcm_qa_ct](#ct-philips-gantry); [dcm_qa_philips_enh](#mri-philips-enhanced) |
| Canon / Toshiba | [Credence Cartridge Radiomics Phantom](#ct-credence-phantom); [dcm_qa_canon](#mri-canon) — Toshiba-labelled CT; Canon-labelled MRI. |
| United Imaging | [dcm_qa_uih](#mri-united-imaging) |

## Transfer-syntax and Enhanced multi-frame tests

| Source / vendor and model | Contents | Transfer syntax | Size | Source licence or terms | Registration / access |
| --- | --- | --- | --- | --- | --- |
| <a id="syntax-jpeg2000"></a>[JPEG 2000 lossless](https://github.com/pydicom/pydicom/tree/main/src/pydicom/data/test_files)<br>not stated | One 64 × 64 MR decoder fixture, derived from the small NEMA-based MR test image. Files: [`MR_small_jp2klossless.dcm`](https://github.com/pydicom/pydicom/blob/main/src/pydicom/data/test_files/MR_small_jp2klossless.dcm). | JPEG 2000 Image Compression (Lossless Only) (`1.2.840.10008.1.2.4.90`) | 6,008 bytes (1 stored file; manifest total) | ["MIT License"](https://github.com/pydicom/pydicom/blob/main/LICENSE) (repository) | **No.** Public GitHub files; no registration needed. |
| <a id="syntax-htj2k"></a>[HTJ2K](https://github.com/pydicom/pydicom-data/tree/master/data_store/data)<br>not stated | Two 480 × 640 RGB decoder fixtures; clinical modality and scanner not stated. Files: [`HTJ2KLossless_08_RGB.dcm`](https://github.com/pydicom/pydicom-data/blob/master/data_store/data/HTJ2KLossless_08_RGB.dcm), [`HTJ2K_08_RGB.dcm`](https://github.com/pydicom/pydicom-data/blob/master/data_store/data/HTJ2K_08_RGB.dcm). | High-Throughput JPEG 2000 Image Compression (Lossless Only) (`1.2.840.10008.1.2.4.201`); High-Throughput JPEG 2000 Image Compression (`1.2.840.10008.1.2.4.203`) | 628,842 bytes (2 stored files; manifest total) | ["MIT License"](https://github.com/pydicom/pydicom-data/blob/master/LICENSE) (repository) | **No.** Public GitHub files; no registration needed. |
| <a id="syntax-jpegls"></a>[JPEG-LS near-lossless](https://github.com/pydicom/pydicom/tree/main/src/pydicom/data/test_files)<br>not stated | 100 × 100 RGB secondary-capture color patterns with line and sample interleave. Files: [`SC_rgb_jls_lossy_line.dcm`](https://github.com/pydicom/pydicom/blob/main/src/pydicom/data/test_files/SC_rgb_jls_lossy_line.dcm), [`SC_rgb_jls_lossy_sample.dcm`](https://github.com/pydicom/pydicom/blob/main/src/pydicom/data/test_files/SC_rgb_jls_lossy_sample.dcm). | JPEG-LS Lossy (Near-Lossless) Image Compression (`1.2.840.10008.1.2.4.81`) | 2,222 bytes (2 stored files; manifest total) | ["MIT License"](https://github.com/pydicom/pydicom/blob/main/LICENSE) (repository) | **No.** Public GitHub files; no registration needed. |
| <a id="syntax-rle"></a>[RLE lossless](https://github.com/pydicom/pydicom/tree/main/src/pydicom/data/test_files)<br>not stated | 100 × 100 RGB secondary-capture color patterns, one- and two-frame variants. Files: [`SC_rgb_rle.dcm`](https://github.com/pydicom/pydicom/blob/main/src/pydicom/data/test_files/SC_rgb_rle.dcm), [`SC_rgb_rle_2frame.dcm`](https://github.com/pydicom/pydicom/blob/main/src/pydicom/data/test_files/SC_rgb_rle_2frame.dcm). | RLE Lossless (`1.2.840.10008.1.2.5`) | 4,702 bytes (2 stored files; manifest total) | ["MIT License"](https://github.com/pydicom/pydicom/blob/main/LICENSE) (repository) | **No.** Public GitHub files; no registration needed. |

Syntax assignments and image dimensions are supported by the maintainer's [pixel reference tests](https://github.com/pydicom/pydicom/blob/main/tests/pixels/pixels_reference.py) and [UID registry](https://github.com/pydicom/pydicom/blob/main/src/pydicom/_uid_dict.py). These are small decoder fixtures, not complete studies. The [test-file provenance notice](https://github.com/pydicom/pydicom/blob/main/src/pydicom/data/test_files/README.txt) describes mixed origins and some identifier replacement; it is not a per-file privacy certification. The HTJ2K source likewise provides no per-file de-identification statement. Repository MIT licences and upstream notices must be read together.

| Additional test | Existing source | Scope |
| --- | --- | --- |
| Enhanced multi-frame MRI | [dcm_qa_xa30](#mri-siemens-xa30) | Siemens MR XA30 enhanced exports; transfer syntax not stated. |
| Classic versus Enhanced MRI | [dcm_qa_philips_enh](#mri-philips-enhanced) | Philips exports of the same acquisitions; transfer syntax not stated. |

Enhanced multi-frame describes a DICOM object structure, **not a transfer syntax**. The RLE two-frame secondary-capture fixture does not establish Enhanced MR/CT support. This selection covers HTJ2K UIDs ending in `.201` and `.203`, not `.202`; JPEG-LS coverage here is near-lossless `.81`, not lossless `.80`.

## NIfTI samples

| Source / vendor and model | Contents | Transfer syntax | Size | Source licence or terms | Registration / access |
| --- | --- | --- | --- | --- | --- |
| <a id="nifti-minimal"></a>[Minimal NIfTI-1 ramp](https://nifti.nimh.nih.gov/nifti-1/data/)<br>not stated | Synthetic minimal image with a ramp along Y; single .nii or paired .hdr/.img files. | not applicable | not stated | ["terms not stated"](https://nifti.nimh.nih.gov/nifti-1/data/) | **No.** Public file links; no registration requested. |
| <a id="nifti-mni152"></a>[MNI152 LR/RL reference images](https://nifti.nimh.nih.gov/nifti-1/data/)<br>not stated | Two averaged T1 atlas references, 91 × 109 × 91 at 2 mm; .nii.gz or paired .hdr.gz/.img.gz. | not applicable | not stated | ["terms not stated"](https://nifti.nimh.nih.gov/nifti-1/data/) | **No.** Public file links; no registration requested. |

The [NIfTI reference page](https://nifti.nimh.nih.gov/nifti-1/data/) supplies LR/RL variants for orientation checks. Neither scanner attribution, byte sizes nor sample-specific reuse terms are given. NIfTI is a separate format and has no DICOM transfer syntax.

## Excluded and unverified candidates

These are research leads, **not recommended or verified downloads**. No candidate is counted in the 17 entries.

| Candidate source | Status | Reason |
| --- | --- | --- |
| [Planmeca Viso G7 knee phantom](https://zenodo.org/records/12722386) | excluded | 538.3 MB of MATLAB projection data from a knee phantom; not dental DICOM or NIfTI. |
| [360 Visualise CBCT demo scans](https://360v.co.uk/which_cbct/) | unverified | Scan ZIP links (206 MB, 188 MB, 220 MB) exist, but sample-specific vendor/model, DICOM format and de-identification are not established. Installer links are outside scope. |
| [Morita One Volume Viewer demo dataset](https://cavendishimaging.com/cbct-support/software-downloads/) | unverified | A demo is listed under Morita Accuitomo, but standalone DICOM contents, privacy and reuse terms are not confirmed. |
| [NNT demo dataset](https://cavendishimaging.com/cbct-support/software-downloads/) | unverified | Demo link exists, but standard DICOM contents, privacy and separation from proprietary viewer material are not confirmed. |
| [Class 3 malocclusion listing](https://medimodel.com/sample-dicom-files/) | unverified — detail page not opened | The publisher listing was opened, but the Class 3 malocclusion detail page could not be verified (timeout / HTTP 403). Sample-specific size, vendor, terms and registration remain unverified. |

## How to open these on iPhone/iPad or in a browser

On iPhone or iPad, save permitted sample files to Files and import them into a compatible viewer, such as the [Ossidex iOS app](https://ossidex.com/). For a browser option, the [free Ossidex browser viewer](https://ossidex.com/dicom-viewer) accepts local files. Desktop options include [Weasis](https://weasis.org/en/), [3D Slicer](https://www.slicer.org/) and [Horos](https://horosproject.org/).

Keep each DICOM series together when importing. NIfTI support, codecs and Enhanced multi-frame support vary by viewer and version. Follow the dataset's access restrictions when choosing where to process it; the PhysioNet entry is not an unrestricted demo. These samples are for testing and research, not clinical decisions.

## Contributing and licence

See [CONTRIBUTING.md](CONTRIBUTING.md) for evidence requirements and corrections.

The index text and original catalogue descriptions are licensed under [CC BY 4.0](LICENSE). External datasets, software, source quotations and trademarks retain their own terms. This index does not relicense them.

