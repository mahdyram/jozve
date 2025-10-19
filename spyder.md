این خطا کاملاً مشخص است: **Spyder برای اجرای کد در محیط `myenv-2` نیاز به پکیج `spyder-kernels` دارد** و نسخه مناسب آن نصب نشده است.

---

### راه حل:

1. **فعال کردن محیط `myenv-2`**:

```bash
conda activate myenv-2
```

2. **نصب spyder-kernels نسخه مناسب**:

با Conda:

```bash
conda install spyder-kernels=3.0
```

یا با pip:

```bash
pip install "spyder-kernels==3.0.*"
```

> دقت کن نسخه باید **>=3.0.0 و <3.1.0** باشد تا با Spyder سازگار باشد.

3. بعد از نصب، **Spyder را دوباره باز کن** و تست کن. حالا console باید بدون مشکل باز شود و کدها با محیط `myenv-2` اجرا شوند.

<!-- -------------------------------------------- -->
<hr style="height:5px; background-color:red" />
<!-- -------------------------------------------- -->
