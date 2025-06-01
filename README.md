# customer-segmentation-dashboard

## Project Structure & Data Organization

1. **Create the recommended folder structure:**
   ```sh
   mkdir -p notebooks data
   ```
   - `notebooks/`: For Jupyter notebooks documenting each project phase.
   - `data/`: For raw and processed data files (e.g., CSVs).

2. **Download the dataset:**
   - Use the following Python code to download the e-commerce dataset from Kaggle:
     ```python
     import kagglehub
     path = kagglehub.dataset_download("carrie1/ecommerce-data")
     print("Path to dataset files:", path)

3. **Create and activate the virtual environment:**
   ```sh
   python3 -m venv myenv
   source myenv/bin/activate
   ```

4. **Install dependencies:**
   ```sh
   pip install -r requirements.txt
   ```

5. **Run the Jupyter notebooks as needed.**