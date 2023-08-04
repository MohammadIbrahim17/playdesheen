name: Update Page

on:
  push:
    branches:
      - main  # ضع اسم الفرع الذي تريد أن تُحفظ التغييرات فيه

jobs:
  update:
    runs-on: ubuntu-latest
    
    steps:
    - name: Checkout Repository
      uses: actions/checkout@v2
    
    - name: Update Page Content
      run: |
        echo "Mohammad Ibrahim" > new-content.txt
        cat new-content.txt > your-page-file.html  # ضع اسم ملف الصفحة الخاصة بك هنا
        
    - name: Commit Changes
      run: |
        git config --local user.email "github-actions[bot]@example.com"
        git config --local user.name "GitHub Actions"
        git commit -am "Update page content"
    
    - name: Push Changes
      uses: ad-m/github-push-action@master
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
