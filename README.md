# SCATR

Official code for **SCATR: Mitigating New Instance Suppression in LiDAR-based Tracking-by-Attention via Second Chance Assignment and Track Query Dropout** (WACV 2026). [[Paper]](https://openaccess.thecvf.com/content/WACV2026/papers/Cheong_SCATR_Mitigating_New_Instance_Suppression_in_LiDAR-based_Tracking-by-Attention_via_Second_WACV_2026_paper.pdf)

LiDAR-based tracking-by-attention (TBA) models suffer from new instance suppression: track queries win the assignment, so newly appearing objects are missed and false negatives stay high. SCATR adds two architecture-agnostic training strategies:

- **Second Chance Assignment** concatenates unassigned track queries to the proposal queries before bipartite matching, giving them a second chance to match a ground-truth object.
- **Track Query Dropout** diversifies the supervised query configurations so the decoder learns to handle missing and newborn tracks.

On nuScenes tracking, SCATR outperforms previous LiDAR-based TBA methods by 7.6% AMOTA and closes the gap to tracking-by-detection.

## Usage

Build the container with `make docker-build`, then train and evaluate with the main config:

```bash
bash local_train.sh projects/configs/scatr-temporal_lidar.py
bash local_test.sh projects/configs/scatr-temporal_lidar.py <checkpoint.pth>
```

## Citation

```bibtex
@inproceedings{cheong2026scatr,
  title     = {{SCATR}: Mitigating New Instance Suppression in {LiDAR}-based Tracking-by-Attention via Second Chance Assignment and Track Query Dropout},
  author    = {Cheong, Brian and Wang, Letian and Papais, Sandro and Waslander, Steven L.},
  booktitle = {Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision (WACV)},
  year      = {2026}
}
```

## License

See `LICENSE` for this project's code and `THIRD_PARTY_NOTICES.md` for code adapted from other projects.
