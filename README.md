# منصة قطوف الخير — WhatsApp CRM MVP

منصة Web عربية لإدارة محادثات WhatsApp Cloud API والعملاء والموظفين والمتابعات والطلبات والتقارير.

## ما تم تنفيذه

- حسابات وصلاحيات Admin / Supervisor / Agent.
- صندوق محادثات واستقبال Webhooks وحالات الرسائل.
- ملفات العملاء والتوزيع والملاحظات وTags.
- المتابعات والطلبات ومؤشرات المبيعات.
- استيراد وتصدير Excel وCSV.
- تقارير الموظفين والعملاء والمبيعات.
- قوالب Meta والردود الجاهزة وأخطاء الإرسال.
- إشعارات داخلية ونسخ احتياطي وتجهيز إنتاج.
- فحص جاهزية واختبار تشغيلي UAT قبل الربط الحي.

## تشغيل محلي

```bash
cp .env.example .env
docker compose up --build
```

ثم افتح `http://localhost:8000` وأنشئ مديرًا:

```bash
docker compose exec web python manage.py createsuperuser
```

## تشغيل إنتاجي

استخدم `.env.production.example` و`docker-compose.prod.yml` واتبع:

- `docs/DEPLOYMENT_AR.md`
- `docs/ARCHITECTURE_AR.md`

يبقى وضع WhatsApp التجريبي مفعلًا حتى إدخال بيانات Meta واختبار الرقم التجريبي.

## فحص الجاهزية قبل التجربة

```bash
python manage.py operational_check
python manage.py pilot_smoke_test
```

على سيرفر الإنتاج استخدم:

```bash
python manage.py operational_check --production --check-redis
```

راجع `docs/PILOT_UAT_AR.md` و`docs/GO_LIVE_CHECKLIST_AR.md`.
