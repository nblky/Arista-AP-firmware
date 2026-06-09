# Firmware unpack output

Source firmware packages: ../18/<model>/upgrade_bundle.tgz.enc

Directory layout:
- <model>/extracted/dtb/       Extracted DTB files plus decompiled DTS and dumpimage metadata.
- <model>/extracted/bdf/       BDF / board-data / bdwlan / caldata-related files copied from rootfs, preserving rootfs paths.
- MANIFEST.tsv                 Counts of extracted DTB and BDF-related files by model.
- DTB_FILES.tsv                Extracted DTB file list.
- BDF_FILES.tsv                Extracted BDF-related file list.
