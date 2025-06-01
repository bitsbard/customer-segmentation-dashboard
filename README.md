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
     ```
   - Copy the `data.csv` file from the downloaded path to your project's `data/` directory:
     ```sh
     cp /path/to/downloaded/data.csv data/
     ```
     Replace `/path/to/downloaded/data.csv` with the actual path printed by the script above.

3. **Create and activate the virtual environment:**
   ```sh
   python3 -m venv myenv
   source myenv/bin/activate
   ```

4. **Install dependencies:**
   ```sh
   pip install -r requirements.txt
   ```

5. **Run your scripts or Jupyter notebooks as needed.**

---

This structure ensures transparency and reproducibility for each step of the project. All data processing and analysis steps are documented in the `notebooks/` directory, and raw/cleaned data is stored in `data/` for easy access and review.
