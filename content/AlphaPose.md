
# Inference
- Input image: any size
- Detector:
	- Yolo:
		- Default config for INP_DIM = 608
		- image_preprocess -> turning to a Torch tensor of shape [1, 3, 608, 608] for feeding into the network (`yolo_api.py` line `69`)
			- First one seems to be batch number (how many images)
			- Second is RGB
		- images_detection -> (`yolo_api.py` line `77`)
			- collect bbox w.r.t original image size
			- Output: `dets(torch.cuda.FloatTensor,(n,(batch_idx,x1,y1,x2,y2,c,s,idx of cls)))`: human detection results
			- Use the network to predict a bunch of boxes, then only keep human (class label = 0) and use [[Non Maximum Suppression|NMS]] to remove redundant boxes.
	- image_postprocess -> (`detector.py`)
		- `inps[i], cropped_box = self.transformation.test_transform(orig_img, box)`
			- For each box, clip the box and resize to `cfg.DATA_PRESET.IMAGE_SIZE` (`256x192`) which is also the input dimension for the Pose Estimation network 
				- if you use `256x192_res50_lr1e-3_1x.yaml` then the input dimension is `256x192`
- Pose Estimation
	- If use `256x192_res50_lr1e-3_1x.yaml`
		- Input `num_boxes x 3 x 256 x 192`
		- Output Heatmap of size `num_joints x 64 x 48`
			- Each joint is a channel (output of the last nn.Conv2D layer)

# Train
- Loss: 
	- MSELoss:
		- Dataset: From joints_3D, iterate each joint and create heatmap for each joint
		- For each joint that is **visible**, calculate MSE Loss between the output of the NN and the created heatmaps
		- ! So in order to train a subset of joints only, we can like set the other joints visibility to 0