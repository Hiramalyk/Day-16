# Day-16
import os, shutil, argparse

def organize(folder):
    for file in os.listdir(folder):
        path = os.path.join(folder, file)
        if os.path.isfile(path):
            ext = file.split('.')[-1]
            ext_folder = os.path.join(folder, ext)
            os.makedirs(ext_folder, exist_ok=True)
            shutil.move(path, os.path.join(ext_folder, file))

parser = argparse.ArgumentParser()
parser.add_argument("folder", help="Folder to organize")
args = parser.parse_args()

organize(args.folder)
