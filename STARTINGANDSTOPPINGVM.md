# Starting and Stopping a VM Instance

- [Google documentation: Stop or restart a Compute Engine instance](https://docs.cloud.google.com/compute/docs/instances/stop-start-instance)
  - This official documentation from Google is a guide on how to stop and start your VM instance on Google Cloud; it is particularly helpful to use if you get stuck in a connection loop while trying to connect with your SSH in-browser terminal (after authorization).

## Outline

- In this how-to guide, you will learn how to start and stop your VM instance. After navigating to your Google Cloud VM Instances portal, you will see that the VM can be stopped and started from the "More actions" drop-down menu. After your instance has resumed, you should be able to connect to your SSH in-browser terminal. **See below for detailed steps:**

### Step 1: Stopping the VM
- **Stop** your VM. Do this by navigating and clicking the **3 dots** on the right-hand side of "Connect"
<img width="470" height="140" alt="Screenshot Open 3 Dots" src="https://github.com/user-attachments/assets/b4272c51-bd16-4727-afdf-6b269924494f" />

### Step 2: Stop
- Click **"Stop"**
<img width="975" height="463" alt="image" src="https://github.com/user-attachments/assets/4c87aebe-7b41-400d-912a-8efae5aee107" />

### Step 3: Skip graceful shutdown
- A pop-up will appear. Check **"Skip graceful shutdown (if applicable)"** and click **"Stop"**
<img width="975" height="514" alt="image" src="https://github.com/user-attachments/assets/0ff5d223-3082-4d1c-9022-c156e894a987" />
  - Once VM is fully stopped, you will no longer see a green checkmark under "Status." This new symbol will show:
  <img width="231" height="303" alt="image" src="https://github.com/user-attachments/assets/f7f7c3b5-8100-4db4-89f0-422c6926b95c" />

### Step 4: Start/Resume
- **Start** your VM again; Press the 3 dots on the right-hand side of "Connect" and press **"Start/Resume"**
<img width="497" height="774" alt="image" src="https://github.com/user-attachments/assets/f41fe5fb-b20f-4ce5-8e68-e048f51c24f6" />

### Step 5:
- A pop-up will appear asking if you are sure you want to start the VM. Press **"Start"**
<img width="975" height="410" alt="image" src="https://github.com/user-attachments/assets/c22149e1-6c42-4955-8b89-d2a34e33f07a" />

### Step 6: Connect to SSH browser
- Once your VM has started again, a **green checkmark** should appear under "Status." Click the **arrow** under "Connect" and next to "SSH." A drop-down menu will appear. Click **"Open in browser window"**
<img width="902" height="443" alt="Screenshot Open SSH " src="https://github.com/user-attachments/assets/158a422b-22b7-4658-a3cd-cba437b5e09c" />

### Step 7: Authorize
- Click **"Authorize"** and your terminal should open! **Good luck!**
<img width="975" height="491" alt="image" src="https://github.com/user-attachments/assets/75c31481-ccb4-4417-867c-67e3986d6536" />

## Conclusion
- Starting and stopping your VM instance allows it to reset. This minimizes the chance that your SSH in-broswer terminal will not connect after authorization! No more connection loops! 
