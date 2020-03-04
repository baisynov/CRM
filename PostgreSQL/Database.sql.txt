create table pledged_property_laptops(
id serial primary key,
lap_cpu varchar,
year_lap integer,
display double precision,
core_speed integer,
memory varchar,
lap_gc varchar,
lap_harddisc varchar,
drive_unit varchar
);

create table pledged_property_pc(
id serial primary key,
motherboard varchar,
cpu varchar,
ram varchar,
graphics_card varchar,
memory_gc varchar,
hard_disc varchar,
cd_rom varchar,
case_pc varchar,
usb boolean,
lan boolean,
wi_fi boolean,
psu varchar
);

create table application(
id serial primary key,
time_of_application timestamp not null,
full_name varchar(70) not null,
date_of_birth date,
phone_number integer not null,
laptop_id integer references pledged_property_laptops(id),
pc_id integer references pledged_property_pc(id)
);

create table base_for_rings(
id serial primary key,
applicant_id integer references application(id) not null,
call_price integer,
date_rings timestamp not null,
laptop_id integer references pledged_property_laptops(id),
pc_id integer references pledged_property_pc(id)
);

create table concluded_contact(
id serial primary key,
time_currently timestamp not null,
applicant_id integer references application(id) not null,
given_cash integer not null,
taken_cash integer not null,
deadline date not null
);

create table payment(
id serial primary key,
applicant_id integer references application(id) not null,
payment_cash integer not null,
remain integer not null,
payment_date date not null
);